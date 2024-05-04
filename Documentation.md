**This a projects highlight steps required to design and implement a pipeline using Jenkins to automate the deployment of a web application.The aim of this project is to be able to implement CI/CD actions on the application using Jenkins**

**Pre-requisite**

* Basic Knowledge of Jenkins and git
* Understanding Jenkins, installation, building freestyle project and pipeline project

**Deliverable**

* Detailed Documentation for each Jenkins components setup
* Explanation of steps and messures implemented in each steps

**Details:**
### 1. **Jenkins Server Setup:**

* Install Java Development Kit (JDK):
* Download and install the JDK appropriate for your operating system.
* Set up the JAVA_HOME environment variable.
* Download and Run Jenkins:
* Download the Jenkins WAR file from the official website.
* Run java -jar jenkins.war to start Jenkins.

### 2. **Source Code Management Repository Integration for Jenkins:**

**Navigate to Jenkins Job Configuration:**
   * - Open Jenkins and navigate to the configuration page of the desired Jenkins job.

**Select Source Code Management Section:**
   * - In the job configuration, locate the "Source Code Management" section.

**Choose Version Control System (VCS):**
   * - Select the appropriate VCS option from the dropdown menu (e.g., Git, SVN).

**Configure Repository URL:**
   * - Enter the URL of the repository where your source code is hosted.

**Provide Credentials (if required):**
   * - If the repository requires authentication, provide the necessary credentials (e.g., username and password, SSH key).

 **Specify Branches to Build:**
   * - Specify the branches to be built by Jenkins (e.g., master, develop).

**Save Configuration:**
  * - Save the job configuration to apply the changes.

**Trigger Builds Automatically:**
   * - Optionally, configure build triggers to automatically start builds when changes are detected in the repository.

** Test the Configuration:**
   * - Trigger a build manually or wait for changes to trigger an automatic build to verify that the integration is working correctly.

**Monitor Build Results:**
    * - Monitor the build console output and job status to ensure that Jenkins is successfully fetching the source code from the repository and executing the build process.


### 3. **Jenkins Freestyle Job for Build and Unit Test:**

**Create a New Freestyle Project:**
  * - Log in to Jenkins and click on "New Item" to create a new freestyle project.

**Configure Source Code Management:**
 * - In the job configuration, under "Source Code Management," select the version control system (e.g., Git, SVN) and provide the repository URL.

**Define Build Steps:**
  * - Scroll down to the "Build" section and click on "Add build step."
  * - Choose the appropriate build tool (e.g., Maven, Gradle) or shell script to compile your code.

**Add Unit Test Execution Step:**
 *  - Click on "Add build step" again and choose the option to execute unit tests.
 *  - Specify the command or script to run your unit tests (e.g., `mvn test`, `npm test`).

**Configure Post-Build Actions:**
  *  - Scroll down to the "Post-build Actions" section and click on "Add post-build action."
  *  - Choose options such as archiving artifacts, sending email notifications, or triggering downstream jobs based on build results.

**Save and Run the Job:**
  *  - Save the job configuration and click on "Build Now" to manually trigger a build.
  * - Monitor the build console output for any errors or failures during the build and unit test execution.


### 4. **Setup Jenkins Pipeline for Web Application:**

 **Create a New Pipeline Job:**
 *  - Log in to Jenkins and click on "New Item" to create a new pipeline job.

 **Define Pipeline Script:**
 *  - In the job configuration, select "Pipeline" as the job type.
 *  - Choose either "Pipeline script" or "Pipeline script from SCM" as the pipeline definition method.
 *  - If selecting "Pipeline script," write the pipeline script directly in the Jenkins job configuration.
*   - If selecting "Pipeline script from SCM," specify the repository URL, credentials (if required), and the path to the Jenkinsfile containing the pipeline script.

**Write Jenkinsfile:**
   - Create a Jenkinsfile in the root directory of your web application project.
*   - Define stages for your pipeline, such as "Build," "Test," "Deploy," etc., and specify the necessary steps for each stage.
   - Use Jenkins Pipeline syntax (e.g., `pipeline`, `stage`, `steps`) to define the pipeline stages and steps.

**Configure Source Code Management (Optional):**
 *  - If not using "Pipeline script" as the pipeline definition method, configure source code management (e.g., Git) in the Jenkins job configuration.
   - Specify the repository URL, credentials (if required), and the branch to use.

**Configure Build Triggers (Optional):**
*   - Set up build triggers to automatically start the pipeline when changes are detected in the repository (e.g., polling SCM, webhooks).

 **Save and Run the Pipeline:**
 *  - Save the pipeline job configuration.
 * - Click on "Build Now" to manually trigger the pipeline execution.
 *  - Monitor the pipeline execution in the Jenkins dashboard and review the console output for any errors or failures.

###  5. **Setup Jenkins Pipeline for Web Application with Docker Image Creation and Registry Push:**

**Create a New Pipeline Job:**
*  - Log in to Jenkins and click on "New Item" to create a new pipeline job.

**Define Pipeline Script:**
*   - In the job configuration, select "Pipeline" as the job type.
*  - Choose either "Pipeline script" or "Pipeline script from SCM" as the pipeline definition method.

**Write Jenkinsfile:**
*   - Create a Jenkinsfile in the root directory of your web application project.
*  - Define stages for your pipeline, including stages for building, testing, Docker image creation, and registry push.
*   - Use Jenkins Pipeline syntax to define each stage and the necessary steps within each stage.

**Configure Source Code Management (Optional):**
*   - If not using "Pipeline script" as the pipeline definition method, configure source code management (e.g., Git) in the Jenkins job configuration.
*  - Specify the repository URL, credentials (if required), and the branch to use.

**Docker Image Creation Stage:**
*   - Define a stage in the Jenkinsfile for building the Docker image of your web application.
*   - Use Docker commands or Dockerfile to build the image, tag it appropriately, and store it in the local Docker registry.

**Registry Push Stage:**
*   - Define another stage in the Jenkinsfile for pushing the Docker image to a container registry.
*   - Use Docker commands to authenticate with the container registry (if required) and push the image to the specified repository.

 **Configure Docker Credentials (Optional):**
*   - If authentication is required to push images to the container registry, configure Docker credentials in Jenkins.
*   - Go to "Manage Jenkins" > "Manage Credentials" and add Docker username and password credentials.

**Save and Run the Pipeline:**
*   - Save the pipeline job configuration.
*   - Click on "Build Now" to manually trigger the pipeline execution.
*   - Monitor the pipeline execution in the Jenkins dashboard and review the console output for any errors or failures.


###  **process for running a container**

**A container is a lightweight, standalone software package containing code, runtime, system tools, libraries, and settings needed to run an application independently. They offer application isolation and consistency across various computing environments.**

*  To run a container:
*  Pull Docker Image: Use the `docker pull` command to download the Docker image from a container registry.

*  Run Container: Execute the `docker run` command to start a new container instance based on the pulled image. Specify options like port mappings, volume mounts, environment variables, and container name.

* . Access Container: Use `docker exec` to access the container via the command line or interactively. For example, to access the container shell: `docker exec -it <container_id> /bin/bash`.

*  Manage Container: Use Docker commands like `docker start`, `docker stop`, `docker pause`, or `docker rm` to manage the container's lifecycle. Monitor logs and resource usage with `docker logs` and `docker stats`.

*  Exit Container: Use the appropriate exit command (e.g., `exit` or `Ctrl + D`) to exit the container shell or interactive mode


### **setup for pushing images to a registry 


**Install Docker:**
*   - Ensure Docker is installed on your system. Follow the installation instructions for your operating system from the Docker documentation.

**Login to Container Registry:**
*   - Use the `docker login` command to authenticate with the container registry where you want to push your images. Provide your username and password when prompted.

*     docker login <registry_url>
  

**Tag Docker Image:**
*   - Tag the Docker image you want to push with the registry URL. You can tag an existing image or tag it during the build process.
 
*     docker tag <image_name>:<tag> <registry_url>/<image_name>:<tag>
   
**Push Docker Image:**
*   - Use the `docker push` command to push the tagged image to the container registry.
    
*  docker push <registry_url>/<image_name>:<tag>
    
*  Replace `<registry_url>` with the URL of your container registry, `<image_name>` with the name of your Docker image, and `<tag>` with the desired tag for your image.

* Example:bash
* docker login docker.io
* docker tag my-image:latest docker.io/myusername/my-image:latest
* docker push docker.io/myusername/my-image:latest


**Ensure you have the necessary permissions to push images to the registry. Additionally, some registries may require additional configurations or authentication methods, such as API tokens or SSH keys. Refer to the documentation of your container registry for specific setup instructions.**


