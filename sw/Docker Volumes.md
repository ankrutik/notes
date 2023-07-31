Tags: #docker 

- Provide file system for docker containers
- ` docker volume create <volume_name>`
- ` docker run -dp 127.0.0.1:3000:3000 --mount type=volume,src=<volume_name>,target=/etc/todos <image_name>`

# Links

# References
https://docs.docker.com/get-started/05_persisting_data/