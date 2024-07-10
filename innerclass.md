# Inner Class

 * introduced in **1.1** version.
 * at first it was introduced as a part of Event handeling to fix the GUI bugs as a part of Event Handeling but because of this powerful features and benfits of inner class, slowly programmer have started using it in the day to day basis.

***

## What is inner class and when we should go for Inner class?

***Declaring a class within another class*** is called Inner class.

1. Inner class can access all acess modifier.
2. Every Inner class have HAS-A relationship with the outer class,
3. Inner classes are allowed to create method, method, variable, contructors and blocks. 

When without existance of one type of object, if another object could not exist then in that case we go for **inner class concept**.

EXAMPLE:

 1. Suppose we have an university and the university is having various departments for studies. In that case if the unniversity is ot existing then we can't have the departments in it. So, now let's convert it into Object Oriented Programming-
        
```
class University //outer class
{
    class Department //inner class
        {
            //code
        }
}
```
2. Now let's take an JAVA feature example, in Java we have a concept called**MAPS**. So, Maps is basically a collection of keys and values and each of those key-value pair is called an**Entry**.Without the existance of map there is no existance of Entry. Hence, Entry interface is Written within the Map interface.

```
interface Map
{
    interface Entry
    {
        //code
    }
}
```
>NOTE 1:- Without the existance of the outer class object there is no exitance of the inner class object.

>NOTE 2:- The relation between the outer and the inner class is not ~~**is-a**~~ relationship rather it follows **HAS-A** relationship (Composition and Agregation).

## Types of Inner classes-

***Based on the position and declaration of Behaviour***, Inner classes are Categorized to following types:-
1. Normal /Regular Inner Class(inner class)
2. Method/Local Inner Class
3. Anonymous Inner Class
4. Static Inner Class/ Static Nested Class

![types of inner classes](https://www.theprogrammerguide.com/img/java/innerClassTypes.png)

### 1. Normal/Regular Inner Class -

* If we declare a named class, directly inside a class without any *static* keyword is called ***Normal/regular Inner Class***.

*  We can declare both **static and non-static** datamembers inside the inner class.

* Directly we can't create object for non-static inner class. We can create **inner class** object **using outer class reference**.

* We can create `main()` inside **non-static inner class**, we can run non-static method inner class.

Example-

```
Outer.java

class Outer 
{
    class Inner
    {
        //code
    }
}
```

So, **when we compile** `Outer.java` file; 

>then two bytecodes are generated i.e. `Outer.class` and `Outer$Inner.class`.

When we **run** `Outer.java` file;

>then at runtime we will get RunTimeError: **NoSuchMethodError:main** fro both the bytecodes.

#### Accessing the inner class

As we know that the inner class is present inside os the outer class hence, for to access the inner class we need to first access the outer class. To understand this let's fo through a program for inner class.

```
public class A 
{
	class B
	{
		int i=10;
		static int j=20;
		void m1()
		{
			System.out.println("M1-b");
		}
		static void m2()
		{
			System.out.println("m2-b");
		}
	}
	public static void main(String[] args) {
		System.out.println(A.B.j);
		A.B.m2();
		
		new A().new B().m1();
	}
}
```

So, in the above we have a file created as `A.java`, this file is to understand the concept of inner class. So in this file as we can see that we are having,

* `class A` wic is the **Outer Class** And `class B` which is the **Inner Class**.

* Inside the `class B` we are having **non-static** datamember i and non-static method `m1()`. We also are having **Static** datamember j and static method `m2()`.

* In `main()` when we need to acess the ***Static Datamembers*** then;
>``System.out.println(A.B.j);``
>> this tells go to A class then go to B class and then print j variable, as here j is static hence no object creation is required.

>``A.B.m2();``
>> this tells go to A class then go to B class and then access `m1()`.

* We can access the ***Non-Static Datamembers*** in the following ways:
    
    ````
    //way1:
		A a= new A();
		A.B b= a.new B();
		System.out.println(b.i);
		b.m1();
    ````

    ````
    //way 2:
		A.B b1= new A().new B();
		System.out.println(b1.i);
		b1.m1();
    ````

    ````
    //way 3:
		new A().new B().m1(); //once used is removed from the heap area.
    ````
* Within the inner class `this` always refers to the inner class object. If we want to refer the outer class object then we need `outer_class_name.this` to access the outer class object.
````
public class Outer 
{
	int x=10;
	class Inner
	{
		int x=100;
		public void m1()
		{
			int x=1000;
			System.out.println(x);
			System.out.println(this.x);
			System.out.println(Outer.this.x);
		}
	}
	public static void main(String[] args) {
		new Outer().new Inner().m1();
	}
}
````

>**Output**
````
1000
100
10
````

#### Modifiers allowed for inner classes-
1. public
2. default
3. final
4. staticfp
5. abstract
6. private 
7. protected
8. static

***