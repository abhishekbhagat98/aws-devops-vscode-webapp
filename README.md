# ☁️ Set Up a Web App in the Cloud

This project demonstrates how to deploy a Java-based web application on an AWS EC2 instance using VSCode and Maven. It was completed as part of the [NextWork DevOps Challenge](https://learn.nextwork.org/projects/aws-devops-vscode).

## 🔁 Data Flow Diagram

Below is the high-level architecture of this project:

![Data Flow](./data-flow-web-app-setup.png)

## 📌 Project Overview

The objective was to:

- Launch an EC2 instance on AWS.
- Connect to the instance using VSCode's Remote-SSH.
- Install Java and Maven on the EC2 instance.
- Generate a Java web application using Maven.
- Explore and edit the application using VSCode.

## 🛠️ Tools & Technologies

| Tool/Service       | Purpose                                  |
|--------------------|------------------------------------------|
| **AWS EC2**        | Virtual server to host the web app       |
| **VSCode**         | Code editor with Remote-SSH capabilities |
| **Maven**          | Build automation tool for Java projects  |
| **Java (Corretto 8)** | Java Development Kit for the application |

## 🚀 Steps to Reproduce

### 1. Launch an EC2 Instance

1. Use the AWS Console to launch a new EC2 instance.
2. Choose Amazon Linux 2023 AMI.
3. Select `t2.micro` instance type.
4. Create a new key pair (e.g., `nextwork-keypair.pem`) and download it.
5. Configure the security group to allow SSH (port 22) from your IP.

### 2. Set Up VSCode

1. Install [Visual Studio Code](https://code.visualstudio.com/).
2. Install the **Remote - SSH** extension.
3. Configure SSH in VSCode by adding the following to your SSH config file:

    ```bash
    Host my-ec2-instance
         HostName <EC2_PUBLIC_IP>
         User ec2-user
         IdentityFile ~/.ssh/nextwork-keypair.pem
    ```

4. Connect to the EC2 instance via VSCode.

### 3. Install Java and Maven on EC2

1. Update the package manager:

    ```bash
    sudo yum update -y
    ```

2. Install Java (Amazon Corretto 8):

    ```bash
    sudo yum install java-1.8.0-amazon-corretto -y
    ```

3. Install Maven:

    ```bash
    sudo yum install maven -y
    ```

### 4. Generate Java Web Application

1. Use Maven to generate a web application:

    ```bash
    mvn archetype:generate \
         -DgroupId=com.nextwork.app \
         -DartifactId=nextwork-web-project \
         -DarchetypeArtifactId=maven-archetype-webapp \
         -DinteractiveMode=false
    ```

2. Navigate to the project directory:

    ```bash
    cd nextwork-web-project
    ```

### 5. Explore and Edit in VSCode

1. In VSCode, open the `nextwork-web-project` folder.
2. Explore the project structure:
    - `src/main/webapp`: Contains HTML, JSP files.
    - `pom.xml`: Maven configuration file.

## 📎 Documentation

For a detailed walk-through with step-by-step notes, refer to:

[📄 Cloud Web App Setup.pdf](./Cloud%20Web%20App%20Setup.pdf)