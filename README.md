# Get Started with Glassfish
GlassFish is a Java EE application server which is hosted on Java.net and mainly sponsored by Sun Microsystems. GlassFish usually has full support of the latest Java EE related JSRs. It is accessible both under GPL and CDDL licenses.

# Audience
This tutorial is intended for programmers interested in developing and deploying Java EE 7 applications. It covers the technologies comprising the Java EE platform and describes how to develop Java EE components and deploy them on the Java EE Software Development Kit (SDK).

# Pre-requisites
Before proceeding with this tutorial, make sure all hardware and software requirements are met then install Glassfish.
[Installation Guide](https://docs.oracle.com/cd/E26576_01/doc.312/e24935/installing.htm#GSING00002)
[Download Glassfish](https://javaee.github.io/glassfish/download)

## h2

* liste1
* liste2
  * sous lise
  * sous liste2
  
  
1. numer1
1. number 2
1. number 3
   1.2 toto
   1.3 titit
   
   
```java

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.annotation.WebServlet; 
import javax.servlet.*;
import javax.servlet.http.*;

@WebServlet(urlPatterns={"/hello"})
public class HelloWorld extends HttpServlet {

  
    public void doGet(HttpServletRequest req, HttpServletResponse res)
            throws IOException, ServletException {
        
        PrintWriter pw = res.getWriter();
        try {
			pw.println("Hello World !<br>");
  		} catch(Exception e) {
        	e.printStackTrace();
        }
    }
}
```

> un encadré
> de plus


