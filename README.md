# Get Started with Glassfish
GlassFish is a Java EE application server which is hosted on Java.net and mainly sponsored by Sun Microsystems. GlassFish usually has full support of the latest Java EE related JSRs. It is accessible both under GPL and CDDL licenses.

# Audience
This tutorial is intended for programmers interested in developing and deploying Java EE 7 applications. It covers the technologies comprising the Java EE platform and describes how to develop Java EE components and deploy them on the Java EE Software Development Kit (SDK).

# Pre-requisites
Before proceeding with this tutorial, make sure all hardware and software requirements are met then install Glassfish.    
[Installation Guide](https://docs.oracle.com/cd/E26576_01/doc.312/e24935/installing.htm#GSING00002)   
[Download Glassfish](https://javaee.github.io/glassfish/download)

## GlassFish Documentation
GlassFish documentation: There is plenty of documentation which will help you to get started or to continue with using GlassFish.<br />
Some of the most important:  
GlassFish tech tips master index:
 [Link](https://glassfish.dev.java.net/public/TipsandBlogs.html)  
GlassFish Wiki:
 [Link](http://wiki.glassfish.java.net/)
 
## What is GlassFish?

## GlassFish Example: HelloWorld.java
* Start by creating new JAVA EE application:
	1. Launch NetBeans IDE.
	2. File --> New Project -- > Java EE --> Enterprise Application
	3. ProjectName: HelloWorld
	![Image1](https://github.com/saadaibrahim/Glassfish/blob/master/PIC1.png)
	4. Expand HelloWorld-war and under SourcePackages create a new Servlet using below sample piece of code:	
```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet(urlPatterns = {"/helloworldservlet"})
public class helloworldservlet extends HttpServlet {

    protected void processRequest(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        try (PrintWriter out = response.getWriter()) {
            out.println("<!DOCTYPE html>");
            out.println("<html>");
            out.println("<head>");
            out.println("<title>Hello World </title>");            
            out.println("</head>");
            out.println("<body>");
            out.println("<h1>Hello World at " + request.getContextPath() + "</h1>");
            out.println("</body>");
            out.println("</html>");
        }
    } 
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }
    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        processRequest(request, response);
    }
    @Override
    public String getServletInfo() {
        return "Short description";
    }
}
```
* Deploy HelloWorld Application:  
  * Before deploying your application, you have to start GlassFish server.
    * Under "services", expand Servers, write click "GlassFish Server 4" and choose start.
    * Wait until the GlassFish start successfully, then deploy your application.
  * To check if your application was built successfully, you can either check the Output Window result or check if your      application is added under glassfish -- Applications:      
    *![Image2](https://github.com/saadaibrahim/Glassfish/blob/master/pic2.png)  
      
 ## Starting the Administration Console 
 To administer GlassFish Server and manage users, resources, and Java EE applications, use the Administration Console tool. 
 GlassFish Server must be running before you invoke the Administration Console.
 1. To start the Administration Console, open a browser at: 
> http://localhost:4848
 2. To Start the Administration Console Using NetBeans IDE
  2.1 Click the Services tab.
  2.2 Expand Servers.
  2.3 Right-click the GlassFish Server instance and select View Domain Admin Console.
  Note: NetBeans IDE uses your default web browser to open the Administration Console.
 ![Image3](https://github.com/saadaibrahim/Glassfish/blob/master/pic3.png) 
 
 ## Deploying an Application Using the Administration Console 
 You can deploy applications by using the graphical Administration Console.
 Before you begin, at least one GlassFish Server domain must be started before you deploy the sample application.
 1. Launch the Administration Console
 2. Click the Applications node in the tree on the left. 
     The Applications page is displayed.
 3. Click the Deploy button.
    The Deploy Applications or Modules page is displayed.
 4. Select Packaged File to be Uploaded to the Server, and click Browse.
 5. Navigate to the location in which you saved the helloworld.war sample, select the file, and click Open.
    You are returned to the Deploy Applications or Modules page.
 6. Specify a description in the Description field, for example: HelloWorld-war
 7. Accept the other default settings, and click OK.
    You are returned to the Applications page.
 8. Select the check box next to the hello application and click the Launch link to run the application.
    The default URL for the application is:
    > http://localhost:8080/HelloWorld-war/
    ![Image4](https://github.com/saadaibrahim/Glassfish/blob/master/pic4.png)  
    
 ## To View Deployed Applications in the Administration Console
 1. Launch the Administration Console
 2. Click the Applications node in the tree on the left. 
 Expand the node to list deployed applications. Deployed applications are also listed in the table on the Applications page.
 
 ## To Undeploy the Sample Application Using the Administration Console
 1. Launch the Administration Console
 2. Click the Applications node in the tree on the left. 
 The Applications page is displayed.
 3. Select the check box next to the HelloWorld sample application. 
 4. Remove or disable the application.
   4.1 To remove the application, click the Undeploy button
   4.2 To disable the application, click the Disable button.
 
 >Refer to the Administration Console online help for additional information.
 
