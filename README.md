Task Documentation
==========
### Version Control:
Store the UI library code in a private Git repository. This allows for version control, collaboration, and tracking changes.

### Build and Publish (CI/CD Pipeline):
#### Configure the pipeline to:

1- Clone the repository.

2- Install dependencies using npm install.

3- Build the library.

4- Create a Docker image based on a React base image.

5- Include the built UI library as a dependency in the Dockerfile.

6- Build the Docker image and push it to a container registry.


### Usage in Applications:

1- In your application's package.json, add the UI library as a dependency and specify the version.

2- Run npm install install the library.

3- Import the library's components into your application's code and use them as needed.

#### Or

if you want to use the library in microservice you can use the image we built as the container image.

Scripts and tools
==========

### Create Library:
```
npx create-react-app my-ui-library --template typescript
```
### Store the UI library code in a private Git repository:
```
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/samahalisaber/Library.git
git push -u origin main
```
### Configure CI/CD Pipeline using Jenkins

1- configure kubernetes cloud plugin in jenkins (add EKS url, token for authentication)

2- configure pipeline script from SCM (add repository url, credentials, script path)

3- configure Jenkinsfile with stages (Build, Create Docker Image and Push Docker Image) and variable image tag depends on the build number.

4- we can add another stage to deploy this docker image in deployment yaml file if we have any microservice needed to be deployed on kubernetes cluster for example.


