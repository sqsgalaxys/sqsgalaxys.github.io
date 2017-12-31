---
title: Java Reflect
date: 2016-08-09 12:38:42
update:
tags: Java
---


----

<!-- more -->

## `Class.forName()`
1. 创建两个类:狗类、猫类继承父类动物接口,并实现其叫喊方法.
2. 创建一个测试类,通过传入不同动物的名称输出其叫声.比如狗就是汪汪,猫就是喵喵.

### 定义动物借口

```
package com.sqsgalaxys.testReflect;

public interface Animal {
	public void scream();
}

```

### 定义猫类

```

package com.sqsgalaxys.testReflect;

public class Cat implements Animal {

	@Override
	public void scream() {
		System.out.println("miao,miao");
	}
}

```

### 定义狗类

```

package com.sqsgalaxys.testReflect;

public class Dog implements Animal {

	@Override
	public void scream() {
		System.out.println("wang,wang");
	}
}

```

### 不使用反射的写法的测试类

```

package com.sqsgalaxys.testReflect;

public class AnimalTest {
	Animal animal = null;

	public void makeNoise(String flag) {
		if ("狗".equals(flag)) {
			animal = new Dog();
			animal.scream();
		} else if ("猫".equals(flag)) {
			animal = new Cat();
			animal.scream();
		} else if ("羊".equals(flag)) {
			// animal = new Sheep();
			// animal.scream();
		}
		// else if .....
		else {
			System.out.println("没有发现任何动物");
		}
	}

	public static void main(String[] args) {
		AnimalTest at = new AnimalTest();
		// 输出猫的叫声
		at.makeNoise("猫");
	}
}

```

### 使用反射的写法的测试类

```

package com.sqsgalaxys.testReflect;

public class AnimalTestEx {
	Animal animal = null;

	public void makeNoise(String animalName) {
		try {
			animal = (Animal) Class.forName(animalName).newInstance();
		} catch (InstantiationException |
                IllegalAccessException |
                ClassNotFoundException e) {
			e.printStackTrace();
		}
		animal.scream();
	}

	public static void main(String[] args) {
		AnimalTestEx at = new AnimalTestEx();
		at.makeNoise("com.sqsgalaxys.testReflect.Cat");
	}
}

```

## `Class.forName() newInstance() getDeclaredMethod() `
## `invoke() getDeclaredField() setAccessible()`
## `....`


#### 待反射获取的类`Student`

```

package com.sqsgalaxys.testReflectEx;

public class Student {  
    private int age;  
    private String name;  
    public int getAge() {  
        return age;  
    }  
    public void setAge(int age) {  
        this.age = age;  
    }  
    public String getName() {  
        return name;  
    }  
    public void setName(String name) {  
        this.name = name;  
    }  
      
    public static void hi(int age,String name){  
        System.out.println("大家好，我叫"+name+"，今年"+age+"岁");  
    }  
}


```

#### 测试类`Test`

```

package com.sqsgalaxys.testReflectEx;

import java.lang.reflect.Field;
import java.lang.reflect.InvocationTargetException;
import java.lang.reflect.Method;

public class Test {
	@SuppressWarnings({ "unchecked", "unused" })
	public static void main(String[] args)
			throws IllegalAccessException, IllegalArgumentException, InvocationTargetException, InstantiationException,
			ClassNotFoundException, NoSuchMethodException, SecurityException, NoSuchFieldException {
		// 反射使用的三个步骤:
		// 1. 得到要调用类的 class
		// 2. 得到要调用的类中的方法
		// 3. 方法调用 (invoke)

		// JAVA反射的常规使用步骤
		Class<?> cls = Class.forName("com.sqsgalaxys.testReflectEx.Student");

		Method m = cls.getDeclaredMethod("hi", new Class[] { int.class, String.class });
		m.invoke(cls.newInstance(), 21, "test");
		// 方法调用中的参数类型
		// 正确调用
		// Method setMethod = cls.getDeclaredMethod("setAge", Integer.class);
		// setMethod.invoke(cls.newInstance(), 15);
		// 不正确调用
		// Method setMethod = cls.getDeclaredMethod("setAge", int.class);
		// setMethod.invoke(cls.newInstance(), 15);
		// 异常信息
		// Exception in thread "main" java.lang.NoSuchMethodException:
		// com.sqsgalaxys.testReflectEx.Student.setAge(int)
		// at java.lang.Class.getDeclaredMethod(Unknown Source)
		// at com.sqsgalaxys.testReflectEx.Test.main(Test.java:**)

		// 参数类型要一致

		// static方法的反射调用
		// static方法调用时，不必得到对象实例
		// Method staticMethod = cls.getDeclaredMethod("hi", int.class,
		// String.class);
		// staticMethod.invoke(cls, 20, "test");
		// staticMethod.invoke(cls.newInstance(), 21, "test");

		// private 的成员变量赋值
		// 直接赋值
		// Object student = cls.newInstance();// 得到一个实例
		// Field field = cls.getDeclaredField("age");
		// field.set(student, 10);
		// System.out.println(field.get(student));
		// 异常信息
		// Exception in thread "main" java.lang.IllegalAccessException: Class
		// com.sqsgalaxys.testReflectEx.Test can not access a member of class
		// com.sqsgalaxys.testReflectEx.Student with modifiers "private"
		// at sun.reflect.Reflection.ensureMemberAccess(Unknown Source)
		// at java.lang.reflect.AccessibleObject.slowCheckMemberAccess(Unknown
		// Source)
		// at java.lang.reflect.AccessibleObject.checkAccess(Unknown Source)
		// at java.lang.reflect.Field.set(Unknown Source)
		// at com.sqsgalaxys.testReflectEx.Test.main(Test.java:47)
		// private 的成员变量赋值
		// 解决方法1 setAccessible()
		// Object student = cls.newInstance();
		// Field field = cls.getDeclaredField("age");
		// field.setAccessible(true);//设置允许访问
		// field.set(student, 10);
		// System.out.println(field.get(student));

		// private 的成员变量赋值
		// 解决方法2
		// Object student = cls.newInstance();
		// Method setMethod = cls.getDeclaredMethod("setAge", Integer.class);
		// setMethod.invoke(student, 15);// 调用set方法
		// Method getMethod = cls.getDeclaredMethod("getAge");
		// System.out.println(getMethod.invoke(student));

	}
}

```

#### 参考:

- [十八、Java从头开始- Java反射的使用 - ranji13 - ITeye技术网站](http://ranji13.iteye.com/blog/2295269 "")
- [JAVA反射使用手记 - hbcui1984的专栏 - 博客频道 - CSDN.NET](http://blog.csdn.net/hbcui1984/article/details/2719089 "")


