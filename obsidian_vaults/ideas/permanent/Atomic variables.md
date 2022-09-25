# Atomic variables
Tags: #java 
 [[volatile]] keyword solves the [[Visibilty Problem]] which helps in multi-threaded applications. 

If the application goes beyond reading and updates the values, this will create the [[Synchronisation problem ]] which is:
- Thread1 reads the value from memory with the intention of incrementing the same variable
- Thread2 updates the value in memory
- Thread1 does not know about the operation Thread2 performed and writes it's incremented value 

This is solved by using Atomic variables which have functions like `get(), getAndIncrement()` that are thread safe. 


# Links

# References
https://www.baeldung.com/java-volatile-vs-atomic