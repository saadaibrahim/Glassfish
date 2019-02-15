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
  * sous liste2
  
  
1. numer1
1. number 2
1. number 3
   1.2 toto
   1.3 titit
   
   


> un encadré
> de plus


