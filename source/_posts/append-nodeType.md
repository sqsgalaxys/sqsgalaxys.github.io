---

title: $.append nodeType
date: 2017-08-30 18:36:11
update:
tags:

---

# $.append nodeType

```
	append: function() {
		return this.domManip( arguments, function( elem ) {
			if ( this.nodeType === 1 || this.nodeType === 11 || this.nodeType === 9 ) {
				var target = manipulationTarget( this, elem );
				target.appendChild( elem );
			}
		});
	},

```

节点类型	描述	子节点
1	Element	代表元素	Element, Text, Comment, ProcessingInstruction, CDATASection, EntityReference
9	Document	代表整个文档（DOM 树的根节点）。	Element, ProcessingInstruction, Comment, DocumentType
11	DocumentFragment	代表轻量级的 Document 对象，能够容纳文档的某个部分	Element, ProcessingInstruction, Comment, Text, CDATASection, EntityReference
