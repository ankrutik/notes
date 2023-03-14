# Troubleshooting web servers
Tags: #tech 

- Isolate if the error is at browser or server by looking at browser console or network tab
	- [[HTTP Response Codes]] 400 or 500
- Is the failure at routing of the web server like https or f5?
- Is the failure in the application server?
	- Authentication issue?
	- Forbidden to user?
	- Error in server logs?
		- Startup was alright?
	- Error in application logs
		- Log level needs to change
		- Flag log entries by thread ID
	


# Links

# References