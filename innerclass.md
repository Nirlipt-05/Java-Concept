# Inner Class

 * introduced in **1.1** version.
 * at first it was introduced as a part of Event handeling to fix the GUI bugs as a part of Event Handeling but because of this powerful features and benfits of inner class, slowly programmer have started using it in the day to day basis.

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

#### Nesting of inner class

Inside an inner class we can declare another inner class i.e. ***Nesting of the inner class*** is possible.
````
class D
{
	class B
	{
		class C
		{
			public void m1()
			{
				System.out.println("Innermost class method");
			}
		}
	}
}

public class Tester 
{
	public static void main(String[] args) 
	{
		D d= new D();
		D.B b= d.new B();
		D.B.C c= b.new C();
		c.m1();
	}
}
````

### 2. Method Local Inner Class -

* When we declare an ***inner class inside a method***, then those classes are called Method Local Inner Class.
* Also called ***rarely used Inner Class.***
* Will get executed when the method in which it is create is called **(Method called)**.

#### The purpose of Method call-

1. The main purpose of the method local inner class is to  **define the method specific repeatative required functionality**.
2. Method local inner classes are best suited to **meet nested method requirement**.

Example-
````
Suppose we have a program having high Line of code and in that case we want to call a 
funtionality again and again.
So in the case of reusable component we have "method" that is best suited. 
But in java creation of a method inside a method is not allowed hence we have a concept where in we will created a Class of the method specific functionality inside of a method and call it when required again and again.
So, inside method we can't declare a method but inside method we can declare a class and within that class we will declare the method that we want to use.
So, we will create the object of the class and call it.
````
#### Scopes of the Method Local Inner Class-
* As the scope of the method local inner class is very low hence they are ***rarely used***.
* It is having the scope only within the method in which it is declared. It can't be **can't be accessed outside of the method**.

>Anonymous Inner Classes are most commonly used.

````
public class MLICDemo 
{
	public void m1()
	{
		class In
		{
			public static void sum(int x,int y) 
			{
				int sum=x+y;
				System.out.println("The Sum: "+sum);
			}
		}
		In i= new In();
		i.sum(10, 30);
		i.sum(100, 300);
		i.sum(2999, 34);
	}
	public static void main(String[] args) 
	{
		MLICDemo m= new MLICDemo();
		m.m1();
	}
}
````

* ***We can declare Method Level Inner Class inside both instance and static method.***

	If we declare inner class inside --***instance method***-- from that method local inner class, we can access both static & non-static member of the outer class directly.

	If we declare the inner class inside --***Static Method***-- then we can access only static member of the outer class directly from the method local inner class.

*  This the example of the Inner Class accessiblity-
````
public class TEst 
{
	int x=10;
	static int y=20;
	public void m1()
	{
		class Inner2
		{
			public void m2()
			{
				System.out.println(x);
				System.out.println(y);
			}
		}
		Inner2 i= new Inner2();
		i.m2();
	}
	public static void main(String[] args) {
		TEst t= new TEst();
		t.m1();
	}
}
````
***If we declare m1() as static*** ,then we will get the **Compile Time Error** at the line where we will be printing the non-static variable ``x`` and would display *"non-static variable x can't be referenced from the static context"*.

### 3. Anonymous Inner Class-

* Sometimes we declare Inner Class without name and such type of inner class is called Anonymous Inner Class.

* **Nameless Inner Class**.

* **Main Purpose-**
	
	We create Anonymous Inner class only when we are having one time use(instant use).

	There are 3 types of anonymous inner class based on declaration and behaviour=
	
	1. Anonymous inner class that **extends** a class.
	2. Anonymous inner class that **implements** an interface.
	3. Anonymous inner class that **define inside argument**.

#### 1.Anonymous inner class that **extends** a class.=
Whenever we have ***permanent requirement (regular)*** then there we need to go for **top level class** but if we are on-time or ***temporary requirement*** then we need to go for **anonymous inner class**.

***Example-***
````
class Popcorn
{
	public void taste()
	{
		System.out.println("Salty");
	}
}
public class AnonymousICC 
{
	public static void main(String[] args) {
		Popcorn p=  new Popcorn() //it is the child class object.
		{
			public void taste()
			{
				System.out.println("spicy");
			}
		};
		p.taste();
		Popcorn p1= new Popcorn();// This is the popcorn class object.
		p1.taste();
		
		Popcorn p2= new Popcorn()//it is the child class object
				{
					public void taste()
					{
						System.out.println("Sweet");
					}
				};
		p2.taste();
		System.out.println(p.getClass().getName());
		System.out.println(p1.getClass().getName());
		System.out.println(p2.getClass().getName());
	}
}
````

***Output-***

````
Salty
Sweet
innerclass.AnonymousICC$1
innerclass.Popcorn
innerclass.AnonymousICC$2
````

***The generated .class files are-***

1. Popcorn.class
2. Test.class
3. Test$1.class
4. Test$2.class

***Analysis-***

* Popcorn p= new Popcorn(); //here we are creating Popcorn object.
* here the analysis of the below code

````
Popcorn p = new Popcorn()
{
	
};
````
//here, 

i. we are declaring a class that `extends` Popcorn without name ( Anonymous inner class ).

ii. for that child class we are creating an object with the parent reference.

* 
````
Popcorn p = new Popcorn()
{
	public void taste()
	{
		System.out.println("Spicy);
	}
}
````

