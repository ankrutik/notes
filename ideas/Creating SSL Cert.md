# Creating SSL Cert
Tags: 

## Generate Certificate
**On Windows:**
```bash
keytool -genkey -alias tomcat -keyalg RSA -keystore C:\Java\apache-tomcat-8.5.9\keystore\tomcat
```

**On Linux:**
```bash
keytool -genkey -alias tomcat -keyalg RSA -keystore /opt/tomcat/keystore/tomcat
```

## Check certificate 
**On Windows:**
```bash
keytool -list -keystore C:\Java\apache-tomcat-8.5.9\keystore\tomcat
```

**On Linux:**
```bash
keytool -list -keystore /opt/tomcat/keystore/tomcat
```


# Links

# References
https://www.baeldung.com/tomcat