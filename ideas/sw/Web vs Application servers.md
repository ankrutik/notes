# Web vs Application servers
Tags: #java

Application servers have full support for Java EE spec whereas web servers provide only a subset of that.

Few examples of specs available:
- web servers: JSP, Servlets, WebSockets among a few more
- application servers: all of the specs from web servers plus JMS, JAX-RS, JAX-WS, JSON-P, JavaMail, EJB and few more

Tomcat and Jetty are web servers. 
TomEE, Glassfish, Websphere, Geronimo are application servers.

When using a web server, Tomcat for example, the other specs like JAX-RS, JavaMail, JMS, etc can be included in the application by adding third party libraries in the classpath.

# Links


# References
https://www.baeldung.com/java-servers