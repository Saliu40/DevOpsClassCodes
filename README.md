Jenkins CI/CD Deployment to Apache Tomcat
Project Title: 
Automated CI/CD Pipeline for Java Web Application Deployment Using Jenkins and Apache Tomcat

Project Overview
This project demonstrates a fully automated CI/CD pipeline for building and deploying a Java-based web application. The pipeline is implemented using Jenkins, with the final application deployed to a dedicated Apache Tomcat 9 application server running on an Ubuntu Linux environment provisioned via Vagrant and VirtualBox.
The goal of the project is to remove manual deployment steps, ensure reliable software releases, and reduce deployment time through automation and repeatability.

Objectives
Automate the application build process using Maven.
Automatically generate a deployment-ready WAR artifact.
Deploy the application to Apache Tomcat via Jenkins post-build steps.
Maintain isolated and reproducible environments using Vagrant/VirtualBox.
Enforce continuous integration and streamlined delivery.

Architecture Workflow
Developer → GitHub Repository → Jenkins CI Server → Maven Build → WAR Artifact
→ Jenkins Deploy to Container Plugin → Tomcat 9 Server → Application Runs on Port 8080

Key Tools & Technologies
| Category            | Tools Used             |
| ------------------- | ---------------------- |
| CI/CD Automation    | Jenkins                |
| Build Tool          | Maven                  |
| Application Server  | Apache Tomcat 9.0.98   |
| Programming/Runtime | Java (OpenJDK 11 & 17) |
| Virtualization      | Vagrant + VirtualBox   |
| Source Control      | Git / GitHub           |
| OS Environment      | Ubuntu Linux           |

1. Setting Up Tomcat Environment
<img width="939" height="903" alt="Screenshot 2025-01-24 235403" src="https://github.com/user-attachments/assets/7e12830a-f23a-4a2e-a848-6ddeb27e2b32" />
thats our Ubuntu Vagrant file well define to launch a VM where we will be hosting our Tomcat server, opened the neccessary ports for the puropose of this project.
Tomcat is an open source webserver we use to host or run  java based applications. ​
Installing Tomcat on my Ubuntu  VM created using Vagrant & Oracle VM Virtual Box automation
After Launching and ssh into Ur VM, the 1st Command to run as always is to update, and upgrade Ur Vm package manager to the latest. 
then either get a Tomcat installation bashscript to install tomcat on Ur Vm, or put the script on Ur Vagrant file so it can install while launching Ur Vm. to get codes, check Tomcat Docummentation page.

<img width="936" height="723" alt="Screenshot 2025-01-23 214316" src="https://github.com/user-attachments/assets/58cad2fb-c192-40aa-92d4-2521b89091d5" />
Tomcat is up and running on my vagrant vm.

<img width="956" height="1001" alt="Screenshot 2025-01-23 214441" src="https://github.com/user-attachments/assets/6d6caabf-955b-4b48-86a3-5333b6a8c52d" />
running on port 8080 we earlier define and open on our vagfrant file above
<img width="1905" height="1034" alt="Screenshot 2025-01-24 201235" src="https://github.com/user-attachments/assets/18bd39c7-0e6e-412e-96c4-4fa46d3f4969" />
Above is he the manager app section where our web app

2. Setting Up jenkins Server for our Project CICD
we use Ubuntu WSL to Host our Jenkins Server
<img width="960" height="580" alt="Screenshot 2025-01-24 223553" src="https://github.com/user-attachments/assets/5c1d7f59-7694-46e2-8767-6c6c063c9bec" />
Jenkins Server Up, and Running
For installing jenkins, check Jenkins Documentation for the latest code 
will be deployed.
<img width="1920" height="1080" alt="Screenshot (24)" src="https://github.com/user-attachments/assets/f0bdb6ee-124b-4c01-a83f-94d9cc9eeda0" />
jenkins Up and running on Port 8080
get the jenkins default password from Ur Vm to start configuration.

3. Configuring our CICD Project on jenkins
<img width="1920" height="1080" alt="Screenshot (25)" src="https://github.com/user-attachments/assets/e5b0cae4-5ab7-45a0-8f08-c42ba7d86b3c" />
Installing Jenkins Default Plugins to set up the GUI
<img width="1920" height="1080" alt="Screenshot (26)" src="https://github.com/user-attachments/assets/c58d9a83-843c-4fda-b6ce-7ca6fe8d4783" />
Create Jenkins User
<img width="1920" height="1080" alt="Screenshot (27)" src="https://github.com/user-attachments/assets/05adcad2-510e-41a8-920b-76d24b426872" />
Jenkins welcoming page
We are just going to configure Jenkins based on this Project needs only
<img width="1920" height="1080" alt="Screenshot (28)" src="https://github.com/user-attachments/assets/60924fa3-ea71-453a-b027-7bc44aae7ca9" />
Thats Jenkins Default GUI

we start adding the needed plugins for this project
<img width="952" height="810" alt="Screenshot 2025-01-23 212824" src="https://github.com/user-attachments/assets/07f59c0b-bbfe-4d82-9131-77e4274bae45" />
go to manage Jenkins, Available Jenkins, and installed the following plugins:
a. Deploy to container plugins
b. Maven plugins (Maven is needed to build the Java project) as such the plugin will have to be installed since we are automating the process using jenkins

<img width="932" height="954" alt="Screenshot 2025-01-24 232616" src="https://github.com/user-attachments/assets/8eb9ea18-ac9e-491c-ae04-7377f64cc11a" />
add Mavin to tools after installing the plugins> go to manage jenkins >Tools >add Maven and save it for jenkins to recorgnized an used it when running the pipeline.

<img width="917" height="1003" alt="Screenshot 2025-01-24 201913" src="https://github.com/user-attachments/assets/ce9a41bd-82b0-4c74-a646-ac6c8aa80359" />
Creating Our Freestyle Project Pipeline for this our Demo Project
click on new item on Ur jenkins >choose freestyle Project and give the pipeline a tittle 

<img width="935" height="1001" alt="Screenshot 2025-01-24 202104" src="https://github.com/user-attachments/assets/6464178d-7a8a-4c66-9c30-83c54e1aa0f7" />
it takes Us to the pipeline configuration phases where we are to configure our pipeline based on needs
paste the copied Git project Url after selecting Git, we define this pipeline instructing Jenkins to pull the source code from our git rep.
select the git branch our project is in.
Note: we can configure our Jenkins Pipeline to run our codes in 2 diffrent ways:
a. through a well define structured jenkinsfile included on Ur Git repo for jenkins to pull and use
b. by writing the stages directly on the Jenkins pipeline in groovy language

<img width="928" height="865" alt="Screenshot 2025-01-24 202416" src="https://github.com/user-attachments/assets/81aad604-2cfd-4146-ad45-d681603357aa" />
We scroll down to Build step, click on add build step to select invoke top-level maven targets​
select the maven we earlier installed and added to tools,​
add 'clean package' on the goal section. #we are instructing jenkins on what to do with the codes which is to build the code using Maven.

<img width="907" height="994" alt="Screenshot 2025-01-24 202829" src="https://github.com/user-attachments/assets/f25801b5-cb65-4767-bedb-216684bd6015" />

1. scrolled down to post build actions, select deploy war/ear to container,​
2. On the War/ear files section, write 'target/*war' ​
(that’s the name of the artifact it will deploy to tomcat server after maven build).​
3. On the container section, add Tomcat 9.x remote, (depending on the tomcat Version used).​
4. Then I added credential (my tomcat login details​
the last step in adding  tomcat urls,  that is the Urls of the vm my tomcat is running from)​

<img width="883" height="814" alt="Screenshot 2025-01-24 202756" src="https://github.com/user-attachments/assets/f933b45e-48f1-478c-be3d-de64174faade" />
Adding tomcat login details on jenkins Credentials to enable Authentications:​
we go to manage jenkins, locate credentials, click  on add credentials, select global tools, leave  it as username & password under kind.​
Add your tomcat username under username section,​
add password under the password section,​
give it an id on the id section and click on  create.

Time To Build Our Project
<img width="933" height="941" alt="Screenshot 2025-01-25 012426" src="https://github.com/user-attachments/assets/1934df97-f2d8-4e99-b9c4-36c530212483" />
After successfull Configuration, To build Ur Jenkins Job:​
we go to the dashboard, click on the job, and click on  Build now
#Remember, You will encounter errors on the 1st few build based on either typo errors, or other common errors 
always go to Ur Jenkins console output to identify Ur pipeline errors and fix it till U get it right.
#Once U get it right, thats all, Ur pipeline is automated and forever active, you can go further to create a Git Jenkins Webhook, so that git and jekins will bond together for when Developers Make code changes, github will trigered Ur Jenkins to run the pipeline. #U can aslo go a step further to create a slak notifications, or AWS SNS so You can be getting emails when Ur pipeline failed or when theres any errors.

<img width="1808" height="926" alt="Screenshot 2025-01-25 012212" src="https://github.com/user-attachments/assets/aecba058-f7f8-480e-8323-5acf34964a0c" />
my Jenkins Console output after the pipeline successfully run without a single error

<img width="1901" height="1017" alt="Screenshot 2025-01-25 012244" src="https://github.com/user-attachments/assets/8dd62c8a-9b88-477a-9849-9cb605d0659a" />

My jenkins Pipeline fetch the Code from Github, Build the Code Using maven, and deploy Host the application on the Tomcat Server.

<img width="1907" height="1018" alt="Screenshot 2025-01-25 012259" src="https://github.com/user-attachments/assets/0f6dddfd-4a49-4696-8c21-b62c237e1b3d" />

Our WebApp.



