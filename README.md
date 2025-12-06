# MyWebApp

A simple **Java Web Application** built using **Servlets and JSP**, deployed on **Apache Tomcat** and hosted on an **AWS EC2 (Amazon Linux)** instance.

---

## 🚀 Project Overview

This project demonstrates how to:
- Build and package a Java web application (WAR file)
- Deploy it on Apache Tomcat
- Host the Tomcat server on an AWS EC2 instance (Linux)
- Access the app via a public IP or domain

---

---

## ⚙️ Technologies Used

- **Java (JDK 8 or later)**
- **Apache Tomcat 9**
- **Eclipse IDE**
- **AWS EC2 (Amazon Linux)**
- **Secure Copy (SCP) for deployment**

---

## 🧠 How It Works

- `HelloServlet.java` handles HTTP requests and responses.
- `web.xml` maps the servlet to the `/hello` URL.
- `index.jsp` serves as the landing page.
- The app is packaged as a WAR file and deployed to Tomcat’s `webapps` folder.

---

## 🧾 Servlet Example

```java
package com.example;

import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class HelloServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<h1>Hello from Java Web App running on Tomcat!</h1>");
    }
}

Deployment Steps (AWS EC2)
1.	Launch EC2 instance (Amazon Linux, free tier)
2.	Install Java and Tomcat

sudo yum install java-17-amazon-corretto -y
wget https://downloads.apache.org/tomcat/tomcat-9/v9.0.111/bin/apache-tomcat-9.0.111.tar.gz
tar -xzf apache-tomcat-9.0.111.tar.gz
sudo mv apache-tomcat-9.0.111 /opt/tomcat9

3.	Start Tomcat
/opt/tomcat9/bin/startup.sh

4.	Deploy the WAR file
scp -i "vengat-key.pem" MyWebApp.war ec2-user@<public-ip>:/opt/tomcat9/webapps/

5.	Access app
http://<your-ec2-public-ip>:8080/MyWebApp/hello




