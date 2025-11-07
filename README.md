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
will be deployed.

