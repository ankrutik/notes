# volatile
Tags: #tech #java

The [[Java Memory Model]] uses both the main memory and cache to store shared resources between objects. 

In multi-threaded applications, the value read from cache might be stale as another thread might have updated the value in main memory and the cache was not updated. This is the [[Visibilty Problem]]

The `volatile` keyword solves this by skipping the cache altogether. So reads and writes are to main memory. 


# Links

# References
https://www.baeldung.com/java-volatile-vs-atomic