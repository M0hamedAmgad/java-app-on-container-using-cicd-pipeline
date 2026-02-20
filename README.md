# Automated Java Web Deployment: Jenkins, Docker & AWS 🚀

![AWS](https://imgur.com/Hk28ffE.png)

This project demonstrates a complete **CI/CD Pipeline** implementation to automate the building and deployment of a Java Web Application into a Docker container hosted on AWS EC2.

---

## 📋 Project Overview
The goal of this project is to bridge the gap between development and operations by automating the entire lifecycle:
1. **Source Control:** GitHub
2. **CI Server:** Jenkins (running on AWS EC2)
3. **Build Tool:** Maven
4. **Containerization:** Docker (on a dedicated Docker Host)
5. **Automation:** End-to-end flow from code commit to a running container.

---

## 🛠️ Tech Stack & Tools
| Category | Technology |
| :--- | :--- |
| **Cloud Provider** | AWS (EC2, VPC, Security Groups) |
| **Automation Server** | Jenkins |
| **Containerization** | Docker |
| **Build Management** | Maven |
| **Version Control** | Git & GitHub |
| **App Server** | Apache Tomcat (Docker Image) |

---

## 🏗️ System Architecture
The pipeline is designed to automate the following flow:
* **Jenkins Instance:** Handles the build process, pulls code from GitHub, and runs Maven to generate `.war` artifacts.
* **Docker Host Instance:** Receives the artifacts via SSH and builds a new Docker image using a custom `Dockerfile`, then spins up the application container.

---

## 🚀 Key Features Implemented
* **Custom Docker Images:** Created a tailored Tomcat image to fix the default `webapps.dist` pathing issues.
* **Automated Artifact Transfer:** Used the `Publish Over SSH` plugin to securely move build files between servers.
* **Infrastructure Management:** Configured AWS Security Groups and EC2 environments for DevOps workflows.
* **SCM Polling:** Real-time triggers—any change in the code triggers an immediate automated redeployment.

---

## 📝 Implementation Steps Summary

### 1. Jenkins Setup
* Provisioned an EC2 instance and installed **Java** & **Jenkins**.
* Configured **Maven** and **Git** integrations within Jenkins Global Tool Configuration.

### 2. Docker Host Integration
* Set up a second EC2 instance as a **Docker Host**.
* Created a `dockeradmin` user and configured SSH passwordless authentication.
* Integrated the Docker host with Jenkins using the **Publish Over SSH** plugin.

### 3. Pipeline Automation
* Created a Jenkins job with **Poll SCM** to detect code changes.
* Added post-build steps to build the Docker image and run the container automatically:
```bash
cd /opt/docker;
docker build -t regapp:v1 .;
docker run -d --name registerapp -p 8087:8080 regapp:v1
```
---

## 🏁 Conclusion
* In this project, I successfully automated the build and deploy process using GitHub, Jenkins, Docker, and AWS EC2. This ensures a faster and more reliable release cycle for Java applications.

---

## 🛠️ Author & Community   
I’d love to hear your feedback! Feel free to share your thoughts.  

📧 **Connect with me:**

- **GitHub**: [M0hamedAmgad](https://github.com/NotHarshhaa)    
- **LinkedIn**: [Mohamed Amgad Elgamal](https://www.linkedin.com/in/mohamed-amgad-elgamal)  

---