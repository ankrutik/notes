# Servlets
Tags: #java 

Servlets are **classes that handle HTTP requests**.
A web server will have a **servlet container** in which the servlet class will exist.

Web server receives a request -> forwarded to the servlet container -> forwards it to the servlet class.

At the point of writing this note, the servlets project is published as Jakarta Servlet as the following package
https://mvnrepository.com/artifact/jakarta.servlet/jakarta.servlet-api

## Servlet Class
To declare a class as a Servlet class, the class must `extends HttpServlet`.
This gives access to methods to be overridden like:
- `public void init() throws ServletException`: 
	- must be called successfully (without errors) before requests can be sent to it
	- called only once if the servlet instance is not found by web server
- `public void service(ServletRequest request, ServletResponse response) 
  throws ServletException, IOException`:
	- called when request is received
	- determines the type of HTTP request GET, PUT, POST, DELETE and calls the appropriate method like `doGet(), doPut(), doPost(), doDelete()` respectively
- `public void destroy()`:
	- Called to take the servlet out of service

```ad-tip
Override the service method to include any code for platform level checks like authentication.
```
  
## Servlet configuration

Via annotations
```java
@WebServlet(name = "ABCServlet", urlPatterns = "/calculateServlet")
public class ABCServlet extends HttpServlet {
```

Via xml
```xml
<web-app ...>
    <servlet>
       <servlet-name>ABCServlet</servlet-name>
       <servlet-class>com.root.ABCServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>ABCServlet</servlet-name>
        <url-pattern>/calculateServlet</url-pattern>
    </servlet-mapping>

</web-app>
```


# Links
[[Tomcat]]

# References
https://www.baeldung.com/intro-to-servlets