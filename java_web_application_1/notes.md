Sure, here's a simple example of a Java web application with the scenario you described:

1. Create a new Maven project and add the following dependencies to the pom.xml file:
```
<dependencies>
  <dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
    <scope>provided</scope>
  </dependency>
</dependencies>

```
2. Create a new Java class in the src/main/java directory called HelloWorldServlet with the following code:
```
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/hello")
public class HelloWorldServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        response.getWriter().println("<h1>Hello, World!</h1>");
    }
}

```
3. Create a new JSP file in the src/main/webapp directory called index.jsp with the following code:

```
<!DOCTYPE html>
<html>
<head>
  <title>Hello World</title>
</head>
<body>
  <h1>Hello, World!</h1>
</body>
</html>
```
4. Create a new web.xml file in the src/main/webapp/WEB-INF directory with the following code:
```
<?xml version="1.0" encoding="UTF-8"?>
<web-app version="3.1" xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee 
         http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd">

  <display-name>Hello World</display-name>
  
  <servlet>
    <servlet-name>HelloWorldServlet</servlet-name>
    <servlet-class>HelloWorldServlet</servlet-class>
  </servlet>
  
  <servlet-mapping>
    <servlet-name>HelloWorldServlet</servlet-name>
    <url-pattern>/hello</url-pattern>
  </servlet-mapping>
  
  <welcome-file-list>
    <welcome-file>index.jsp</welcome-file>
  </welcome-file-list>
  
</web-app>

```
5. Build the project using Maven by running the following command in the project directory:
```
mvn package

```

6. The above command should create a target directory inside the project directory with the hello-world-1.0-SNAPSHOT.war file. Deploy this WAR file to Tomcat by copying it to the webapps directory of your Tomcat installation.
7. Start Tomcat by running the bin/startup.bat (or bin/startup.sh) script in the Tomcat installation directory.
8. Access the web application by opening a web browser and navigating to http://localhost:8080/hello-world-1.0-SNAPSHOT/ (assuming that Tomcat is running on port 8080). You should see the "Hello, World!" message displayed on the page.
