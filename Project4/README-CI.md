**Building a web service container:**
  - Explanation and links to web site content
	- The web site content I created using chatgpt consisted of a [index](web-content/index.html) and [about](web-content/about.html) html file that housed the content of the web site and [styles](styles.css) file to handle the apperance and layout. I had to adjust both the index and styles file for my image.
  - Explanation of and link to `Dockerfile`
	- The dockerfile sets up the container environment/base image and copied over our web-content
[Dockerfile](web-content/Dockerfile)
  - Instructions to build and push container image to your DockerHub repository
	- I built the container with `docker build -t larryrsmith/project4:latest .` and pushed using `docker push larryrsmith/project4:latest`. Ok this time I figured it out and used the PAT logining in with `docker login -u larryrsmith` the PAT is safer because they expire.
  - Link to DockerHub repository with your site image
	- [DockerHub repository](https://hub.docker.com/repository/docker/larryrsmith/project4/general)
  - How to run the container that will serve the web application from the image build by the `dockerfile`
	- So first I had to pull the docker image to my instance `docker pull larryrsmith/project4:latest` then all I had to do was run it `docker run -d -p 8080:80 larryrsmith/project4:latest` Host port 8080 container port 80

**GitHub Actions and DockerHub
  - Configuring GitHub Repository Secrets:
	- To create a PAT, I went and logged in to dockerhub. I then went to `account settings` there I clicked on `Personal access tokens` where you can click `Generate new token` to creat the new token for github
	- To create my secrets I went to `github` -> `setting` -> `Secrets and variables` -> `Actions` -> `New repository secret` then filled out what I wanted my new secrets to be.
	- The first secret was my docker user name which will provide my docker user name via the secret. The second holds my PAT to allow github to log into my dockerhub with both the user name and PAT. 
  - CI with GitHub Actions
	- Explanation of workflow trigger
	- Explanation of workflow steps
	- Explanation / highlight of values that need updated if used in a different repository
		- changes in workflow 
		- changes in repository
	- Link to workflow file in your GitHub repository
  - Testing & Validating
	- How to test that your workflow did its tasking
	- How to verify that the image in DockerHub works when a container is run using the image
	- [DockerHub repository](https://hub.docker.com/repository/docker/larryrsmith/project4/general)
