---
title: ideavim 设置面板的简单分析
date: 2018-01-08 01:05:11
tags:
---

![](https://ws2.sinaimg.cn/large/006tNc79gy1fn8jcxhzpxj31401cx13r.jpg)
## The cause of this
本来想写一篇 ideavim 设置中 vim 的快捷键与 idea 本身快捷键的对比,但是经过搜索发现已经有一片类似的博客了:  
[JetBrains IDE Vim 模式的方案 | I sudo X](https://isudox.com/2016/07/26/scheme-of-ideavim-keymap/ '0.0')(这篇博客貌似有个彩蛋:点击页脚眼睛标志旁边的数字)  
注意到设置面板中的 "Shortcut Conflicts for Active Keymap",(活动的Keymap的快捷冲突)  
而且这篇博客中对比的快捷键和我 IntelliJ IDEA 中的 Vim Emulation 设置不太一样
![我的 ideavim 设置面板](https://ws3.sinaimg.cn/large/006tNc79gy1fn8hrga1kzj31kw0zggta.jpg)
所以猜想是不是这个 列表是不是根据快捷键的冲突动态生成的

## 研究过程:
### 1. clone [代码](https://github.com/JetBrains/ideavim.git): [JetBrains/ideavim: Vim emulation plug-in for IDEs based on the IntelliJ platform.](https://github.com/JetBrains/ideavim '0.0')
### 2. 搜索字符串  
找到`VimEmulationConfigurable.java`文件中包含字符串`"Shortcut Conflicts for Active Keymap"`:
``` java
  // com.maddyhome.idea.vim.ui.VimEmulationConfigurable.VimSettingsPanel
  private static final class VimSettingsPanel extends JPanel {
    @NotNull private final VimShortcutConflictsTable myShortcutConflictsTable;

    public VimSettingsPanel(@NotNull VimShortcutConflictsTable.Model model) {
      myShortcutConflictsTable = new VimShortcutConflictsTable(model);
      setLayout(new BorderLayout());
      final JScrollPane scrollPane = new JBScrollPane(myShortcutConflictsTable);
      scrollPane.setBorder(new LineBorder(UIUtil.getBorderColor()));
      final JPanel conflictsPanel = new JPanel(new BorderLayout());
      final String title = String.format("Shortcut Conflicts for Active Keymap");
      conflictsPanel.setBorder(IdeBorderFactory.createTitledBorder(title, false));
      conflictsPanel.add(scrollPane);
      add(conflictsPanel, BorderLayout.CENTER);
    }
  }
```
从中可以看到 `conflictsPanel`,`scrollPane`,`myShortcutConflictsTable` 几个面板的嵌套,最终添加:  
`myShortcutConflictsTable = new VimShortcutConflictsTable(model);`  
找到 `com.maddyhome.idea.vim.ui.VimEmulationConfigurable.VimShortcutConflictsTable#VimShortcutConflictsTable` 的声明:
``` java
    public VimShortcutConflictsTable(@NotNull Model model) {
      super(model);
      getTableColumn(Column.KEYSTROKE).setPreferredWidth(100);
      getTableColumn(Column.IDE_ACTION).setPreferredWidth(400);
      final TableColumn ownerColumn = getTableColumn(Column.OWNER);
      final ComboBoxTableRenderer<ShortcutOwner> renderer = new ShortcutOwnerRenderer();
      ownerColumn.setPreferredWidth(150);
      ownerColumn.setCellRenderer(renderer);
      ownerColumn.setCellEditor(renderer);
    }
```
跟着 renderer 找下去并没有发现什么有关对比快捷键冲突的地方,从`Model`发现`reset()`方法
``` java
    private static final class Model extends AbstractTableModel {
      @NotNull private final List<Row> myRows = new ArrayList<Row>();

      public Model() {
        reset();
      }
      // ....
```
``` java
      public void reset() {
        myRows.clear();
        for (Map.Entry<KeyStroke, ShortcutOwner> entry : VimPlugin.getKey().getShortcutConflicts().entrySet()) {
          final KeyStroke keyStroke = entry.getKey();
          final List<AnAction> actions = VimPlugin.getKey().getKeymapConflicts(keyStroke);
          if (!actions.isEmpty()) {
            myRows.add(new Row(keyStroke, actions.get(0), entry.getValue()));
          }
        }
        Collections.sort(myRows);
      }
```
这里的 `reset()` 方法应该就是获取冲突的快捷键添加到设置面板的表格中的.  
为什么方法名是`reset()` 呢?  

----
从另一个角度来探索:  

## idea 插件添加设置面板
### 1. 创建继承 Configurable 接口的类

```
public class VimEmulationConfigurable implements Configurable {
```

### 2. 重写方法  

createComponent
``` java
  @Override
  public JComponent createComponent() {
    return myPanel;
  }
```
apply
``` java
  @Override
  public void apply() throws ConfigurationException {
    myConflictsTableModel.apply();
  }
```
reset
``` java
  @Override
  public void reset() {
    myConflictsTableModel.reset();
  }
```

isModified
``` java
      public boolean isModified() {
        return !VimPlugin.getKey().getShortcutConflicts().equals(getCurrentData());
      }
```

disposeUIResources
``` java
  @Override
  public void disposeUIResources() {
  }
```


### 3. 插件配置文件中添加配置  
``` xml
  <extensions defaultExtensionNs="com.intellij">
    <applicationConfigurable instance="com.maddyhome.idea.vim.ui.VimEmulationConfigurable"/>
  </extensions>
```
参考:  
[Customizing the IDEA Settings Dialog - IntelliJ IDEA - Confluence](https://confluence.jetbrains.com/display/IDEADEV/Customizing+the+IDEA+Settings+Dialog '0.0')  
[Intellij IDEA插件开发入门 - 西代零零发 - CSDN博客](http://blog.csdn.net/dc_726/article/details/14139155 '0.0')  

在重写的方法中可以看到 reset() 方法:  
``` java
  @Override
  public void reset() {
    myConflictsTableModel.reset();
  }
```
也就是说想看看这个设置面板的快捷键列表的生成可以直接找重写的`reset()`方法  



