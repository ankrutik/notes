Tags: #docker 

- In case your application stack needs needs multiple types of apps, have separate containers for each app.
	- Might want to scale different app types differently.
	- Maintain versions independently
	- Topology on local might have container for testing but on production might be running from existing service
	- Process management is simpler as each container will have just that one process
- Volumes vs Bind Mounts
	- Volumes: file storage for containers
	- Bind Mounts: share host file system into containers
- Use `compose` to create and share multi-container apps
- Image Layering
	- `docker image history <image_name>`

# Links

# References
https://docs.docker.com/get-started/09_image_best/