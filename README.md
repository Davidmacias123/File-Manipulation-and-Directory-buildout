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
