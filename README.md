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

<img width="1055" height="657" alt="image" src="https://github.com/user-attachments/assets/615f6332-1c71-4b3d-b6ed-4ca91c62bd85" />


------------------------------------------------------------------------------------------------------------------------------------



**Pull the official NGINX image:**


Use the Docker command to pull the official NGINX image from Docker Hub:


`sudo docker pull nginx`


Docker will fetch the image if it’s not already available locally. The official NGINX image is widely used and maintained.

<img width="1132" height="288" alt="image" src="https://github.com/user-attachments/assets/e902431c-547f-4488-bb18-1cfde9360b9a" />

--------------------------------------------------------------------------------------------------------------------------------------

**Run the container in detached mode and map port 80**

Launch a container from the NGINX image, mapping host port 80 to container port 80, and run it detached:



`sudo docker run -d -p 80:80 nginx`



`-d` means “detached” (the container runs in the background).


`-p` 80:80 maps host port 80 → container port 80.


This means when you browse to http://localhost on the VM, you should be served by the NGINX container.


<img width="1272" height="662" alt="image" src="https://github.com/user-attachments/assets/aa6416c2-96ef-4476-8cb7-452de3d603df" />


-----------------------------------------------------------------------------------------------------------------------------------

**Verify the web server is running**
On the same VM, test with:


`curl http://localhost`


<img width="1062" height="652" alt="image" src="https://github.com/user-attachments/assets/f9d162a0-5520-4d44-a2e9-5496eddc963b" />



You should see the default NGINX welcome HTML page, starting with <!DOCTYPE html> and the “Welcome to nginx!” header.
You can also open a browser (on the VM) and browse to http://localhost to visually confirm the web page.


<img width="1066" height="658" alt="image" src="https://github.com/user-attachments/assets/d63b4b1a-4496-4e52-9659-2feaa60d00a7" />

------------------------------------------------------------------------------------------------------------------------------------

**Inspect the running container**

List running containers:


`sudo docker ps`


<img width="1011" height="93" alt="image" src="https://github.com/user-attachments/assets/c3c481c1-d995-4083-8cbf-de4293646e40" />



Then pick the container ID and run:



`sudo docker inspect <container-id>`




Inspecting shows detailed JSON output of the container attributes: ports, image, configuration, environment, etc. This is useful for understanding what Docker has arranged under the hood.


<img width="1061" height="661" alt="image" src="https://github.com/user-attachments/assets/01cea807-9422-48de-9cb9-c9f7ad904d92" />



<img width="1066" height="668" alt="image" src="https://github.com/user-attachments/assets/9a967755-8d1a-48cc-9e20-a7751ab88a78" />


-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Stop and remove the container**
Clean up your environment by stopping and removing the container, so the VM remains tidy for future labs:



`sudo docker stop <container-id>`


`sudo docker rm <container-id>`



You can then run sudo docker ps to confirm no containers are running. This is important for sandboxed analysis and avoiding residual state.



<img width="1070" height="671" alt="image" src="https://github.com/user-attachments/assets/ed9b14a6-662b-4d91-8124-b7149bb6d01f" />



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Project Overview**

In this tutorial, I walk through how to deploy a simple NGINX web server using Docker and explore its behavior inside a containerized environment. This lab is designed to help you understand the basics of working with containers, how to expose services to your host machine, and how to inspect what’s happening inside a running container.

By the end of this walkthrough, you’ll know how to run, test, inspect, and clean up a web server container — essential skills for anyone getting started with sandbox analysis or vulnerability scanning in Docker.



-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


**Purpose of This Lab**

The purpose of this lab is to learn how to deploy and explore a containerized web application using Docker. Containers are lightweight, portable environments that make it easy to run applications the same way across different systems. In this exercise, we use NGINX, a popular web server, as our example application to understand how containers work behind the scenes.

By completing this lab, you’ll gain hands-on experience with the entire container workflow — from setup and deployment to inspection and cleanup. You’ll see how Docker can isolate an application from the rest of your system, how ports are mapped to allow web access, and how to manage containers efficiently.

This lab is designed to help you build a foundation in container security and analysis, which is especially useful in environments where applications are tested for vulnerabilities or monitored in sandboxes. Understanding how to deploy and inspect a web server inside a container is a key first step before moving on to more advanced topics, like vulnerability scanning, threat analysis, or custom image building.

In simpler terms, this lab teaches you how to:

Set up a working web server using Docker

Understand how containers run and communicate with your system

Inspect and analyze container configurations

Safely stop and remove containers after testing

By the end, you’ll not only have a running web server inside a Docker container — you’ll also understand why each command is used, how containers operate, and what makes them essential tools for modern cybersecurity and DevOps workflows.





