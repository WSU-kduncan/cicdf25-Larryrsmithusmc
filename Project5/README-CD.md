### Documentation

1. EC2 Instance Details: [Used this yml filr](P5.yml)
  - AMI information 
	- ami-0360c520857e3138f # Ubuntu Server 24.04 LTS (HVM), SSD Volume Type
  - Instance type 
	- t2.micro
  - Recommended volume size
	- I forgot to do this part mine is default 8
  - Security Group configuration
	- I set this to allow home, vpc, and school ips on port 22. I left the SSHparameter in there and it looks like its allowing all to ssh port 22. I also allowed all ips on ports 80, 8080, and 9000 for our container and hooks.
  - Security Group configuration justification / explanation
	- I made sure I would be able to ssh from school and home to the ec2 instance as well as go to our webpage port 8080 and listen for hooks on port 9000.
2. Docker Setup on OS on the EC2 instance
  - How to install Docker for OS on the EC2 instance
	- I set it up in the `P5.yml` file using `sudo apt install -y docker.io` `sudo usermod -aG docker ubuntu` 
  - Additional dependencies based on OS on the EC2 instance
	- I had it `apt update` and install `apt install -y git` just incase but other then that just installed webhook when I got to that part.
  - How to confirm Docker is installed and that OS on the EC2 instance can successfully run containers
	- To test this I did `docker ps -a` then I used my newly created script and it worked wonders. I just visted the website when it completed.
3. Testing on EC2 Instance
  - How to pull container image from DockerHub repository
	- `docker pull larryrsmith/project5:latest`
  - How to run container from image
	- `docker run -d --restart always --name project5 -p 8080:80 larryrsmith/project5:latest` you could run it as -it which allows you access interactivly in a bash shell. I just ran mine in -d detached int he background the whole time because I wasnt really messing with the container itself and would recommend running it this way after testing is done.
  - How to verify that the container is successfully serving the web application
	- Visited the website at http://34.225.80.77:8080
4. Scripting Container Application Refresh
  - Description of the bash script
	- My bash script stops the container, removes the container to free up the container name, pulls the latest container image from dockerhub, and runs a new container in detached mode, set to restart always on ec2 instance start up, with the name project5, on host port 8080 container port 80, from the lastest image pulled.  
  - How to test / verify that the script successfully performs its taskings
	- I tested this by making a small change to my web content then ran the script. When it finished I checked the website for its updates to verify it worked.
  - [Bash script](deployment/deployment.sh)



