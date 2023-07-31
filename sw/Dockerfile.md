Tags: #docker

- Text based file with extension that contains instructions to build docker image
- All instructions ran in this file will be applied as "layers"
- Commands
	- `from <image identifier>`
		- Directive used to mention which base docker image to use
	- `COPY <file from outside image> <location inside image>`
		- Directive to copy files from local file system inside image's file system
	- `WORKDIR`
		- Set certain folder inside image as working directory for any commands that follow
	- `RUN`
		- Command to run while creating image
- 

# Links

# References
https://docs.docker.com/build/guide/intro/#the-dockerfile