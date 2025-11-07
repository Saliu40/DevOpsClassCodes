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
