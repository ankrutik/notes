Tags: #deployment

- Summary
	- Don’t mark instances unhealthy prematurely
	- Don’t wait too long to mark instances healthy
- mistakes
	- Aggregate external health checks into your instance’s health check
	- timeout on health check request
		- Too short
		-  Too long
	- too long a delay before starting health checks to allow traffic

# Links

# References
https://philbooth.me/blog/six-ways-to-shoot-yourself-in-the-foot-with-healthchecks?utm_source=programmingdigest&utm_medium&utm_campaign=1660