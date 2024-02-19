Tags: #docker 

- Refer to this as a [checklist](https://testdriven.io/blog/docker-best-practices/)
- In case your application stack needs needs multiple types of apps, have separate containers for each app.
	- Might want to scale different app types differently.
	- Maintain versions independently
	- Topology on local might have container for testing but on production might be running from existing service
	- Process management is simpler as each container will have just that one process
- Docker File has build steps for your application
	- https://docs.docker.com/build/guide/intro/#the-dockerfile
- Volumes vs Bind Mounts
	- Volumes are file storage for containers
	- Bind Mounts are used to share host file system into containers
- Use `compose` to create and share multi-container apps
- Image building
	- Image Layering
		- `docker image history <image_name>`
	- image caching
	- https://docs.docker.com/get-started/09_image_best/
- Use `entrypoint` over `cmd`
	- https://www.cloudbees.com/blog/understanding-dockers-cmd-and-entrypoint-instructions

# References
https://docs.docker.com/get-started/09_image_best/