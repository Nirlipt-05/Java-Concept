# Servlet-

## Application-

An application is a set of program written to perform a specific task.

### Types od Application-

1. Standalone Application
2. Client Server Application
3. Web Application
4. Hybrid and Native application.

#### 1. Standalone Application=

A Standalone application is a software program designed in such a way that to run this software program, users don't need an internet connection or any server access.

#### 2. Client Server Application=

A client-server application is a program that runs on the client-side while accessing the information over a remote server.

#### 3. Web Application=

Web application is an application which is stored inside the server, can be accessed through the internet over the browser.

#### 4. Hybrid and Native application=

***Native Application=*** These are developed for specific platform or operating systems such as iOS or Android and are installed directly in the device.

***Hybrid Application=*** A hybrid application comibines the element of a native app (an application developed for a specific platform like Android or iOS) and web applications (an appliaction that can be accessed on internet through the browser). It is built in a way that allows dedvelopers to use the same code for all the operating systems.

***Server=***

A server is a computer program which provides service to application and its user (called as client).

## Web Pages-

A web page is a document on the web that is a accessed in a web browser through the internet.

### Types of web page-

There are mainly 2 types of webpages based on functionality:

1. Static webpage
2. Dynamic webpage

#### 1. Static webpages=

Static webpages are the webpages that are already stored in the server.

#### 2. Dynamic Webpages=

Dynamic webpages are the webpage that are generated during the euntime inside the server.

In java we can generate dynamic webpages using Servlets and JSP.

## Web Container-

* A web container is the component of the webserver that interacts with the java servlets.
* Web Container are responsible for managing execution of the servlets and JSP pages for Java EE application.
* Servlets don't have a main(). Web container manages the life cycyle of the Servlet instance.
* When a request comes from the servlet, the server hands the request to the web container.
* Webcontainer is responsible for instantiating the servlet or creating a new thread to handle the request.
* It's the job of the web container yo get the request and response to the servlet.
* The container creates multiple threads to process multiple requests to a single server.

## Difference between web server and application server-

1. **Web server** encompasses *web containers only* whereas **Application server** encompasses *web container as well as EJB container*.
2. **Web server** is useful or fitted for *staic content* but **application server** is fitted for *dynamic content*.
3. **Web server** utilizes *less resource*  whereas **Application sever** utilizes comparatively *more resources*.
4. **Web server** arranges the run environment for *web applications*. While **Application Server** arranges the run environment for *enterprises applications*.
5. *Multithreading* is supported in **web server**, but it is *not supported* in **Application server**
6. **Web server** capacity is *lower* than **application server**.

## What is deployment Descriptor -web.xml file

* A deployment tool is used to **map the HTTP request with the servles**.
* When the web server recieves a request for the application, it uses the deploy descriptor to **map the URL of the request to the code that ought to handel the request.**
* The deployment descriptor should be named as **web.xml**.
* It resides in the application's WAR file under the **WEB-INF/ directory**.

## Description of the elements of the web.xml file-

There are too many elements in the web.xml file. Here the illustration of some elements that is used in the above web.xml file. The elements are as follows:
