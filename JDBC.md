# JDBC

JDBC (Java Data Base Connection) is a Java API for connecting and interacting with databases. JDBC drivers are software components that provides necessary functionality to connect Java applications to different types of databases.
It allows java to communicate with database.
JDBC belongs to JSE. JDBC present inside JDK, by installing JDK we also get JDBC.

## What is API?

* API means *Application Programming Interface*.
* It is an Intermediate between two applications.
* It handels request and its corresponding response.
* Means it is one specification to communicate between any two applications or software component.
* API is nothing but a collection of class and interface.
* JDBC is an API used to connect the java application with it's database, by following some set of specification or rules.

## What is JDBC?

JDBC is an API that defines how a client-
1. connects to the database.
2. sends SQL queries and statements.
3. retrive and manipulate the result.

## Components of JDBC

1. It consists of the set of interfaces and classes written in java.
2. It needs a JDBC driver that vendor implements to comply with JDBC, and database server that supports JDBC.

## Benefits of JDBC

JDBC provides platform independence, security and ease of use for Java developers who needs to access the database.

## JDBC Architecture

![JDBC Architecture](https://i.ibb.co/0tRsgJW/JDBCStructure.png)

* **Client**= A JDBC client is any java application or applet that connectts the server based database using JDBC APIs.

* **Driver Manager**= It is an intermediatary service of the JDBC API that manages the drivers and establish the connection between the JDBC client and the database server.

* **Database Server**= It is a software program that provides sdatabase management functionality within a networked computing environment.

## Why do we need JDBC? 

1. ***Interoperability :*** JDBC provides an universal API for accessing and interacting with any SQL complaint database, regardless of vendors.

2. ***Performance :*** JDBC allows applications to cache data much more efficiently by facilitating the retrieval of multiple rows in one database operation.

3. ***Flexibility :*** JDBC provides flexibility in choosing a vendor-specific or a vendor neutral database management system, allowing developers to adopt new technology.

## There are four types of JDBC drivers-

![JDBC Drives type](https://i.ibb.co/4gnXTN7/JDBCDrivers.png)
1. JDBC- ODBC Bridge Driver.
2. Native-API Partly Java Driver.
3. Network Protocol Pure Java Driver.
4. Thin Driver (Also known as database to database pure driver).

1. JDBC-ODBC Bridge Driver, it is the oldest driver that is being created by using C language, It is the least efficient driver and is not being used now as it is having many issues like performance issues, scalability issues, etc.

2. Native API Partly Java Driver is Vendor specific and it directly doesnot convert the native api call to database specific call. This 
deiver required a library specific to the database being access. Here the API is provided directly by the vendor.

3. In Network protocol driver, it creates a middlelayer that is between the client and the database,hence it is quite slow than thin driver. But as the middle layer is being created, then is consumes some resources thus making it less efficient than thin driver.

4. Thin Driver directly converts the native api call to database calls. It is maximumm efficient.This is the best and more efficient one. It connects directly the client with the database.

> 1. JDBC is a Universal API for Java developers to interact with any SQL complaint Database regardless of vendors.
> 2. Be sure to use `Thin Driver` foe performance abilities while working with the JDBC.
> 3. JDBC have a future i.e. it will continue to play a role in Java ecosystem, with newer versions continually providing developers with powerful and secure access to database.

## JDBC Components

![JDBC Components](https://i.ibb.co/Jq3zxjd/JDBCComponents.png)

In addition to JDBC drivers, there are several other componnts that make up the JDBC API, including:

* `DriverManager` Class
* `Connection Interface`
* `Statements and Prepared Statement Interface`
* `ResultSet Interface`

These components works together to provide a  powerful and flexible API for working with database in java.

### Driver Manager class-

* This is the class present `java.sql` package. 
* This class contains the Database drivers discussed above and   through this Drivers we are able to perform our JDBC tasks.
* It establish connections to the database using the appropriate driver and handels the process of loading the driver class.
* It provides a standardize method for handeling multiple database connections and selecting the appropriate driver.
* It uses a method call `class.forName()` for loading the appropriate drivers to communicate the database.

### Connection Interface-

* This a part of Driver Manager class.
* here we need to give `(url, username, password)`, means the interface will establish connection between database provided it's url, username and password of the database.
* Statement Interface is a part od Connection Interface.
* It has the following usage-
    1. **Creation of Statements-** The connection interface is used to create a statement object, which is used to exeute SQL queries against the database.
    2. **Transaction Management-** The connection interface allows the transaction to be managed with methods such as `commit()` and `rollback()`.
    3. **Retrival of Metadata-**  The Conection interface provides methods to retrieve metadata from database, including information about the database structure and the various objects that are defined in it.

### Statement Interface-

![Statement Interface](https://i.ibb.co/RcYyfDC/Statement-Interface.png)

There are 3 types of statement interfaces i.e.-
1. **Statement**= executes simple SQL queries without parameters and retrieve data.
2. **PreparedStatement**= executes precompiled SQL queries with parameter.More efficient and safe than Statement.
3. **CallableStatement**= executes database stored procedures, here in database stored procedure has precompiled statements.

### Result Set

![Result set](https://i.ibb.co/3MNR2kG/Result-Set.png)

It has the above 3 functionalities.
It helps in retreiving the data that we got through the Statement Interface and stores it.
By the help of this we can-
1. Retrieve the data.
2. Manipulate the data.
3.  Navigate the data.

## Summary/Work Flow of the JDBC components-
> ![Working of JDBC Component](https://i.ibb.co/xLK76Dx/Working.png)

In *DriverManager Class* we have a method call `.getConnecion()` to establish a connection between Database, here the connection will be stored in an instance of *connection interface*.
To run SQL query in java we use *Statements and Prepared Statement Interface*.
The table returned from SQL will be stored as a *ResultSet Interface* instance, and if we want to perform any operation then the operations will be operated on this table.

## SQL Exception-

While we do the above connectivity in JDBC we are prone to various exceptions like the driver my not work, the url will have error, wrong username or password, the query might be wrong,etc.
Hence the **SQLException** class is responsible to handle the exception and errors related to the database interactions. It provides information about the type of error that occured, and allows for more accurate debugging and error resolution.

## Program Flow-

![process flow](https://i.ibb.co/XY6CFDd/processflow.png)

1. We need to connect our IDE with the Database using neccessary connector of the database vendor.
2. We need to load the necessary Drivers.
3. We need to create connection with our database.
4. We need to create Statement Interface instance.
5. Then we need to Execute the query.
6. We need to close the established connection.

## Setting up JDBC-

1. we need SQL installed.
2. we need a Java IDE.
3. we need to intall a connector of SQL.

![My sql Connection](https://i.ibb.co/fntdFq6/msql-Connection.png)

***The Code for Connection of SQLWorkspace to JavaIDE***

![SQLConnectionCode](https://i.ibb.co/XYcrBFr/SQLCnnct-Code.png)

## First JDBC Program-

Steps to do in **MySQL Command line Guide** to create a database=

1. Open **MySQL Command line Guide** and enter your mySQL password.

2. to check the existng database. 

>`show databases;`

3. To create and use the a new database

> `create database --databaseName--;`

> `use --databaseName--;`

4. Now to create a table  in the above database.

> `create table --tableName--;`

Suppose till now we have created a *database*, name : ***mydatabase***
In "mydatabase" we have created a *table* as: ***employees***

5. now we will be defining the column.

The column should be the following:
* id of "int" type.
* name of "VARCHAR(255)" type.
* job_title of "VARCHAR(255)" type.
* salary of "double" type.

```
create table employees(
    -> id INT PRIMARY KEY,
    -> name VARCHAR(255),
    -> job_title VARCHAR(255),
    -> salary DOUBLE
    -> );
```

6. Then we need to `insert` into **employees**.

````
insert into employeees(id, name, job_title, salary) values(
    ->1, 'Nirlipt', 'Java Developer', 70000.0);

insert into employeees(id, name, job_title, salary) values(
    ->2, 'Sagar', 'MERN stack Developer', 65000.0);
````

7. Now if we want to check the table created then
`select * from employees;`

Now as the database is ready then we need to connect it with java using ***JDBC***.

### Important Points to remember-
1. `Class.forName("com.mysql.jdbc.Driver");`-----> Loads *Driver*
2. `Connection con= DriverManager.getConnection(url, username, pw);`----->Establish *Connection*
3. `Statement stmt= con.createStatement();`---->*Statement* Created
4. `ResultSet rs= stmt.executeQuery(query);`----> Executed *SQL query*

* ***DriverManager class*** has a method-----> *getConnection(url, username, password);* this method will connect with the database and has 3 arguments.
Then this method needs to be in a instance of connection type. Hence, we write;
`Connection con= DriverManager.getConnection(url, username, pw);`.

* ***Connection interface*** has a non-static method-----> *createStatement();* this will take no argument.The method is used to create Statement for us & will return the result of ***Statement type***.
Hence, we write;
`Statement stmt= con.createStatement();`.

* ***Statement interface*** has a non-static method---->*executeQuery(---write the query--);* this will have SQL query od string type as argument. This method is used to execute the query.
It will return the result of ***ResultSet type***.
Hence we write,
`ResultSet rs= stmt.executeQuery(query);`

#### first java program to retrieve data from an existing database;

```

package video1.pack1;
/ we will be learning how to fetch the data from the existing database./
import java.sql.*;
public class Main 
{
	public static void main(String[] args) throws ClassNotFoundException 
	{
		//For connection we need url, password, username;
		String url="jdbc:mysql://localhost:3306/mydatabase";
		String username="root";
		String pw= "root";
		String query= "Select * from employees";
		//we need to load the driver
		try {
			Class.forName("com.mysql.jdbc.Driver");
			System.out.println("Drivers Loaded successfully");
		}
		catch (ClassNotFoundException e)
		{
			System.out.println(e.getMessage());
		}
		//now we need to connect
		try
		{
			Connection con= DriverManager.getConnection(url, username, pw);// here connection created
			System.out.println("Connection Established Successfully!!!");
			Statement stmt = con.createStatement();//Statement is created
			ResultSet rs= stmt.executeQuery(query);//query given
			while(rs.next())//means until we have data in rs it will return true and the loop will be kept running
			{
                //here field name is passes of mySQL
				int id= rs.getInt("id");
				String name= rs.getString("name");
                String job_title= rs.getString("job_title");
                Double salary= rs.getDouble("salary");
				System.out.println();
				System.out.println("===================");
				System.out.println("ID: "+id);
				System.out.println("Name: "+name);
                System.out.println("Job Role: "+job_title);
                System.out.println("Salary: "+salary);
			}// here the data is retrived.
			//here we have closed all the opened connection
			rs.close();
			stmt.close();
			con.close();
			System.out.println("Connection Closed Successfully");
		}
		catch (SQLException e)
		{
			System.out.println(e.getMessage());
		}
	}
}

```

#### java program to insert a data to the database-

* here as we are inserting data into database hence we are using a method called `executeUpdate(--query--);` present in ***Statement Interface*** and we need to pass the **query** in the form of string as an **argument**. It will return the ***int type*** data i.e. it will return the numbers of rows affected by our query.

```

int i=stmt.executeUpdate(query);

```
***Note:-***
* if we need to execute a certain query and **fetch** information from the database, then we use `executeQuery();`.
* But when we want to **insert** any data into the database there we use `executeUpdate();`.

***Programs=***

````
package video1.pack1;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

public class insertData 
{
	public static void main(String[] args) throws ClassNotFoundException 
	{
		//For connection we need url, password, username;
		String url="jdbc:mysql://localhost:3306/mydatabase";
		String username="root";
		String pw= "root";
		String query= "insert into employees(id, name, job_title,salary) values (4, 'Manyata', 'Python Developer', 60000.0);";
		//we need to load the driver
		try 
		{
			Class.forName("com.mysql.jdbc.Driver");
			System.out.println("Drivers Loaded successfully");
		}
		catch (ClassNotFoundException e)
		{
			System.out.println(e.getMessage());
		}
		//now we need to connect
		try
		{
			Connection con= DriverManager.getConnection(url, username, pw);// here connection created
			System.out.println("Connection Established Successfully!!!");
			Statement stmt = con.createStatement();//Statement is created
			int rowsaffected =stmt.executeUpdate(query);
			
			if(rowsaffected>0)
				System.out.println("Insert Successfull "+ rowsaffected + " row(s) affected");
			else
				System.out.println("Insertion failed!!");
			stmt.close();
			con.close();
			System.out.println("Connection Closed Successfully");
		}
		catch (SQLException e)
		{
			System.out.println(e.getMessage());
		}
}
}
````

**Output:**
>    Drivers Loaded successfully
>    Connection Established Successfully!!!
>    Insert Successfull 1 row(s) affected
>    Connection Closed Successfully

##### What is Prepaid Statement? How and where to use it.