# Exception Handelling

## What is Exception?

* Exception is not an error but an interruption that will occur during the time of program execution(runtime).
* If we are not getting any desired output and there is no error in the program then we can say that it is caused due to exception.
* When exception occurs then the program terminates abnormally.
* In Java every exception is an class.
* If one exception occurs then the next line of the code is not executed.
* We have two types of exceptions:
    1. **Unchecked Exception**= which is known during runtime.
    2. **Checked Exception**= which is known during compile time.

## 1. Unchecked Exception-

* The exceptions that are **subclass of Runtime Exception** is called Unchecked Exception.
* They are also known as **Compiler Unknown Exception**.
* For unchecked exception the compiler is *not forcing to handel the exception*.
* ***Propagation*** is implicit for unchecked exception.
* ex: ArithematicException, IndexOutOfBoundsException,etc...
* If the problem ***created by other than end user.***

## 2. Checked Exception-

* The exceptions that **aren't the subclass of Runtime Exception** is called Unchecked Exception.
* They are also known as **Compiler Known Exception**.
* *Handeling* is mandatory in checked exception.
* *Compiler forces to handel the checked exception,* if the exception is not handeled then the compiler will throw compile time error.
* ***Propagation*** is explicit for the checked exception.
* ex: FileNotFoundException, IOException, etc...
* If the problem ***created by the end user.***
* ex-
```
import java.io.FileNotFoundException;
import java.io.FileReader;
public class CheckedExceptionExample
{
    public static void main(String[]args)
    {
        System.out.println("Main starts");
        try
        {
            FileReader r= new FileReader("D:\\Core java\\AA.java");---(i)
            System.out.println("Reading Done");
        }
        catch(FileNotFoundException e)
        {
            System.out.println("Handeled");
        }
        System.out.println("Main ends");
    }
}
```
Here in the above program in line no. (i) AA.java file needs to be read in the given location but ther is one possibility where the file might n=be missing in the location given. So, to handel that upcoming exception we need to put it in a try and catch block and as this is a Checked Exception(FileNotFoundException) hence it is mandatory to handel the exception.

## Exception Propagation-

* **Passing an Exception to it's caller method** is called Exception Propagation.
* For *unchecked exception* it is mandatory.
* We can propagate exception using `throws` keyword.
* ***Exeception propagation is not handeling of exception.***
* When the Exception is unknown then we will `throws` to ***Exception class***.
```
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
public class ExceptionPropExample
{
    static void m1() throws FileNotFoundException, IOException
    {
         FileReader r= new FileReader("D:\\Core java\\AA.java");---(i)
         System.out.println("Reading Done");
    }
    public static void main(String[]args)
    {
        System.out.println("Main Starts");
        m1();
        System.out.println("Main ends");
    }
}
```
***When do we need to propagate checked exception?***
We will propagate ***unhandeled checked exception*** by using `throws` keyword.

## All the ***Throwable classes***-

![throwable class hierarchy](https://i.ibb.co/XLmg5Fz/hierarchy-EXCN.png)

All in the boxes are classes and Throwable is the super class for all the other classes. 
* All exceptions except the `runtime exception` are **Checked Exceptions**.
* All the `RuntimeExceptions` are **Unchecked Exceptions**.
* If we are not specific about which type of exception we are encountering then we can directly throw it to `Exception` class.

## Creating an UserDefined Exception-

We can create an Exception of our own by extending our exception to `Exception` class.
````
class AgeInvalid extends RuntimeException
{
    AgeInvalid()
    {
        super("Age is invalid");
    }
}

public class Matrimony
{
    public static void main(String[]args)
    {
        int age=45;
        if(age>=25&&age<=35)
        {
            System.out.println("Eligible");
        }
        else
        {
            AgeInvalidException a= new AgeInvalidException();
            throws a;
        }
    }
}
````

## What is Exception Handelling?

* It is an mechanism used to *continue the flow of execution* (means not provide a solution but to continue the flow).
* To handel exceptions java provides some `keywords`:

    1. try
    2. catch
    3. throw
    4. throws
    5. finally
* Runtime and Compile-time exceptions both are encounterd at runtime only.

### `try`&`catch` block-

* inside "`try` block" we must always write **risky lines**(the lines where there is possiblity of getting exception).
* when the compiler comes across `try` block then it will not execute the try block but the `catch` block will be executed.
* with `try` block there must always be a `catch` block or `finally` block written with. **We can't write try block alone**.
* the exception we get in `try` block is **handeled in the catch block**.
* The best implementation of Exception Handeling is :
    Suppose we are working in an API and there frontend is linked with backend and user enters a value in frontend, the value is sent to the backend and the backend is having some exception and the program terminates abnormally then the user is unaware of it as the exception is not handeled properly. Hence, to avoid this type of situation we need to handel th exceptions by putting the risky lines into the try block and handelling it properly by using the catch block.
* **Syntax**:-
````
try
{
    //risky line written here
}
catch(//exception class instance is created)
{
    //we handle the exception
}
````
#### **Why try and catch is used?**
````
//We are writing a program to take two user input and find the quotient of the numbers.
import java.util.Scanner;

public class ExceptionhandelingDemo
{
    public static void main(String[]args)
    {
        Scanner sc= new Scanner(System.in);
        System.out.println("Enter two numbers: );
        int divident= sc.nextInt();
        int divisor= sc.nextInt();
        int result= divident/divisor;
        System.out.println("The result is: "+result);
    }
}
````
So in the above written code we are expecting the user to enter some numbers and we need to get the quotient of the number.
In that case we have a scenario that the user might enter a number where the divisor might be enterd as `0`, and this will lead to 'ArithematicException'.
Hence, in that case the line where the exception is generated, the program will abnormally terminate and this will lead to inconvinence for the user.
Hence to avoid this type of inconvinence we need to put the risky line in a try-catch block and handel the exception  to continue the flow of execution.
````
import java.util.Scanner;

public class ExceptionhandelingDemo
{
    public static void main(String[]args)
    {
        Scanner sc= new Scanner(System.in);
        System.out.println("Enter two numbers: );
        int divident= sc.nextInt();
        int divisor= sc.nextInt();
       try
       {
         int result= divident/divisor; //as this line was risky line
         System.out.println("The result is: "+result);
       }
       catch(ArithmeticException e)
       {
        System.out.println(e.getMessage());
       }
    }
}
````
> **O/p=** / by zero

#### **We can have multiple try-catch**:

It is used when we know that we can have multiple exceptions.
But after we encounter an exception first then the console don't go fro the next exception i.e. **only one exception will be handeled as the exception is thrown after the first encounter and the program excution stops after that line.**
````
public class ExceptionhandelingDemo
{
    public static void main(String[]args)
    {
        int arr[]= new int[5];
       try
       {
         arr[6]=10/0;-----------(i)
       }
       catch(ArithmeticException | ArrayIndexOutOfBoundsException e)-----(ii)
       {
        System.out.println(e.getMessage());
       }
    }
}
````
>**O/p**- / by zero

So,
    in line (i) we basically have two exceptions i.e. in an array of 5 elements we are trying to access 6th element, hence it is ArrayIndexOutOfBoundsException & we again are having ArithmeticException.
    To handel both the exceptions we are having multiple catch block in line (ii), where we are merging both the catch blocks into a single block by using `or(|)`, so that if we encounter any of the 2 exceptions then we can create an instance of that exception.

**NOTE=**
***There is a convention that while we are giving `try` and multipe `catch` block, then we need to write in a order such that we are first writting a child class exception catch block and followed by immidiate parent class exception, followed by the preceeding parent exception class, if required. This is not mandatory but we need to follow it because when we previously will write the parent exception class then it will handel the exception and the control flow will not get transfered to subsequent child class. Thus, writing the child exception class in the next catch block is of no use***

#### Nested Try-Catch Block-

Here we basically have a try-catch block within another try-catch block.
````
public class ExceptionhandelingDemo
{
    public static void main(String[]args)
    {
        int arr[]= new int[5];
       try
       {
            System.out.println("I am first try block!!");
            try
            {
                arr[6]=10;
            }
            catch(Exception e)
            {
                System.out.println(e.getMessage());
            }
       }
       catch(Exception e)
       {
            System.out.println(e.getMessage());
       }
    }
}
````

***If we have try and catch block then any of the two will get executed, if the try block will execute then the catch block will not and vice-versa.***

***A Catch block can be later followed by a finally block but mandatorily be preceded by a try block.***


### `finally` keyword-

* it is used to **declare finally block**.
* `finally block` will **get executed always irrespective of the exception**.
* `finally block` will be executed *before executing return statement.*
* A `finally block` can't be written alone, for every finally block, a `try-catch` block or a `try` block is mandatory.
* **Advantages=** 
    1. Finally block is used to write important datas or costly resources.
    2. It helps in closing database or file connections.
* **Syntax=**
````
    try
    {
        //risky lines
    }
    catch(Exception e)
    {
        //exception handel
    }
    finally
    {
        //the data that we want to run irrespective of exception.
    }
````
* **example=**
````
public class Ex1
{
    public static void main(String[]args)
    {
        System.out.println("Main Starts");
        System.out.println("DB open");
        try
        {
            System.out.println(10/5);
            return;
        }
        catch(Excepion e)
        {
            System.out.println(e.getMessage());
        }
        finally
        {
            System.out.println("DB close");
        }
    }
}
````
>**O/p-**
````
Main Starts
DB open
2
Main Close
````

### `throw`&`throws` block-

When we want to throw an normal statement as an exception. Then we use `throw` statement.
e.g. if we want to create a program that will take the useer input as age and then check if the entered age is eligible to vote or not. If the person age is greater than 18 then eligible else not.

````
import java.util.Scanner;

public class VoteCheck
{
    public static void main(String[]args)
    {
        Scanner sc= new Scanner(System.in);
        int age= sc.nextInt();
        if(age<18)
        {
            throw new RuntimeException("You are unable to vote!!");
        }
        else
        {
            System.out.println("Eligible");
        }
    }
}
````

#### `throws` keyword-

using `throws` keyword we just give a precautionary that the error might come in a certain block.

````
import java.util.Scanner

public class ExceptionDemo
{
    public static void main(String[]args)
    {
        Scanner sc= new Scanner(System.in);
        int a=sc.nextInt();
        int b= sc.nextInt();
        divisiondemo(a,b);
    }
    public static void divisiondemo(int dividend, int divisor) throws ArithmeticException--------(i)
    {
        System.out.println("the result is: "+dividend/divisor);
    }
}
````

So, as we know that the user might give divisor input as 0.
Hence, we already are taking precaution where in we are throwing the possible exception i.e. line (i), already.