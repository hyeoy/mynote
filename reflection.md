---
title:
---

###

```java OtherTest.java
//1.获取运行时类的父类
Class superClass = clazz.getSuperclass();

//2. 获取运行时类带泛型父类的类型
Type type = clazz.getGenericSuperClass();
//3. <strong>重要 获取运行时类带泛型父类的泛型类型
public void test3(){
    //1. 获取带泛型父类的类型  API把java.lang.String翻译成com.reixz.java.Test<java.lang.String>这个参数化类型的参数
    //2.参数化类型
    ParameterizedType pt = (ParameterizedType)type;
    //3.获取真实的参数类型
    //由于<A,E,T>，所以获取的参数可以有多个，获取的就是一个数组
    Type[] actualTypeArguments = pt.getActualTypeArguments();
    for(){ //class java.lang.String ???为什么有class
        
    }
}
//4.获取运行时类的接口
Class[] interfaces = clazz.getInterfaces();
//5.获取运行时类的内部类
Class[] classes = clazz.getClasses();//不能获取私有的
Class[] classes = clazz.getDeclaredClasses();

//6.获取运行时类的注解
Annotation[] annotations = clazz.getAnnotations();//注意生命周期得是Runtime才能获取
ma.value();//获取注解的值
//7.获取运行时类的包
Package package1 = clazz.getPackage();



```

Interface Type 是所以数据类型的公共父接口，有一个实现类Class

从

```java FieldTest.java
//3.重要 在运行时获取并操作运行时类对象的属性
Person p = clazz.newInstance();
Field age = clazz.getField（"age"）;//在实际操作中，这个属性名我们是不知道，是获取的数据库中的字段名

//1.设置属性值
age.set(p,18);
//2.获取属性值
Object value = age.get(p);

//忽略访问权限
name.setAccessible(true);//私有的直接访问是会报错的，要忽略访问权限，暴力访问
```

```java MethidTest.java
//3.在运行时获取并调用运行时类对象的方法
//获取方法，方法里面有参数列表，每个参数类型要清楚
Class<Person> clazz = Person.class;
Method m1 = clazz.getMethod("eat");//传入方法名、参数，得到Method实例
//基本数据类型也有.class属性，int.class
m1.invoke(p);//invoke()的obj参数是要查看的那个对象
m2.invoke(p,"李四",18,180);//传入实参，返回的是返回值的类型
//void返回null，
//忽略访问权限
```

```java InstanceTest.java
//在运行时获取并调用运行时类的构造器

Constructor<Person> constructor = clazz.getConstructor(String.class,int.class);
constructor.setAccessible(true);
Person p = constructor.newInstance("王文",20)
```



