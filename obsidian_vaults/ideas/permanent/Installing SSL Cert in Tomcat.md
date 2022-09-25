# Installing SSL Cert in Tomcat
Tags: 

See [[Creating SSL Cert]]

In the Tomcat's `server.xml` file, add the following `connector` tag
```xml
<Connector port="8443" protocol="org.apache.coyote.http11.Http11NioProtocol"
  maxThreads="150" SSLEnabled="true" scheme="https" secure="true"
  clientAuth="false" sslProtocol="TLS"
  keystoreFile="C:\Java\apache-tomcat-8.0.23\keystore\tomcat"
  keystorePass="changeit" />
```

# Links
[[Tomcat]]

# References

https://tomcat.apache.org/whichversion.html