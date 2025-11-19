<!-- PROJECT COVER IMAGE -->
<p align="center">
  <img src="https://raw.githubusercontent.com/spring-projects/spring-petclinic/main/src/main/resources/static/resources/images/pets.png" 
       alt="Spring Boot Pet Clinic Banner" width="450"/>
</p>

<h1 align="center">🐾 Spring Boot Pet Clinic Deployment on AWS EC2 (Amazon Linux)</h1>

<p align="center">
  Deploying a production-ready Spring Boot application on AWS EC2 using Amazon Linux, Amazon Corretto, Git, and Maven.
</p>

---

## 📌 Prerequisites

- An active **AWS account**  
- An **EC2 instance** (Amazon Linux 2 or 2023)  
- SSH access to your EC2 instance  

---

## 🚀 Step-by-Step Deployment Guide

### **1️⃣ Update System Packages**
```bash
sudo yum update -y

2️⃣ Install Java Development Kit (JDK)
sudo yum install -y java-25-amazon-corretto-devel


Installs Amazon Corretto (OpenJDK) required for Spring Boot.

3️⃣ Verify Java Runtime
java -version

4️⃣ Verify Java Compiler
javac -version

5️⃣ Install Git
sudo yum install git -y

6️⃣ Verify Git
git --version

7️⃣ Create Project Directory
mkdir springboot_project

8️⃣ Navigate to Directory
cd springboot_project

9️⃣ Clone the Pet Clinic Repository
sudo git clone https://github.com/spring-projects/spring-petclinic.git

🔟 Navigate Into Repository
cd spring-petclinic

1️⃣1️⃣ List All Files
ls -la

1️⃣2️⃣ Ensure Correct Path
cd /home/ec2-user/springboot_project/spring-petclinic

1️⃣3️⃣ Remove Old Builds
sudo rm -rf target

1️⃣4️⃣ Fix File Ownership
sudo chown -R ec2-user:ec2-user .

1️⃣5️⃣ Build the Application
./mvnw package -DskipTests -Dcheckstyle.skip=true -Dmaven.gitcommitid.skip=true

1️⃣6️⃣ Run the Application
./mvnw spring-boot:run


Runs on port 8080.

🔐 Configure Security Group for Access
Step 1: Go to

AWS Console → EC2 → Security Groups

Step 2: Choose Your Instance’s Security Group
Step 3: Add Rule for Port 8080

Type: Custom TCP

Port: 8080

Source:

Your IP (recommended)

0.0.0.0/0 (testing only)

Step 4: Access the Application
http://your-ec2-public-ip:8080

🎉 Final Output

You should see the Spring Pet Clinic homepage running on your EC2 instance.

