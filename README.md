# File-Manipulation-and-Directory-buildout
As a junior security analyst testing containerized environments for sandbox analysis, the task is to deploy a sample web application, monitor its behavior, and document the configuration. This serves as a reference for future vulnerability scanning labs and container deployments to ensure consistent, secure testing environments.

1. Launch the Ubuntu VM and open a terminal
Begin by logging into your Ubuntu virtual machine and opening a terminal window.


2. Verify Docker version and status
In the terminal run:


`docker --version`


`sudo systemctl status docker`



You want to confirm:
Docker is installed and the version is displayed.
The Docker service is active (running) and enabled.
Displaying “active (running)” means the daemon is ready to accept container commands.



Pull the official NGINX image
Use the Docker command to pull the official NGINX image from Docker Hub:


`sudo docker pull nginx`


Docker will fetch the image if it’s not already available locally. The official NGINX image is widely used and maintained.



Run the container in detached mode and map port 80

Launch a container from the NGINX image, mapping host port 80 to container port 80, and run it detached:



sudo docker run -d -p 80:80 nginx



`-d` means “detached” (the container runs in the background).


`-p` 80:80 maps host port 80 → container port 80.


This means when you browse to http://localhost on the VM, you should be served by the NGINX container.


Verify the web server is running
On the same VM, test with:


`curl http://localhost`



You should see the default NGINX welcome HTML page, starting with <!DOCTYPE html> and the “Welcome to nginx!” header.
You can also open a browser (on the VM) and browse to http://localhost to visually confirm the web page.


Inspect the running container

List running containers:


`sudo docker ps`



Then pick the container ID and run:



`sudo docker inspect <container-id>`


Inspecting shows detailed JSON output of the container attributes: ports, image, configuration, environment, etc. This is useful for understanding what Docker has arranged under the hood.




Stop and remove the container
Clean up your environment by stopping and removing the container, so the VM remains tidy for future labs:




`sudo docker stop <container-id>`


`sudo docker rm <container-id>`



You can then run sudo docker ps to confirm no containers are running. This is important for sandboxed analysis and avoiding residual state.
