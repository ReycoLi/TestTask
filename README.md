
1. Technique Stack and Approach Description
Web Dev: SpringMVC 4.2.4 , JSP 2.0, Servlet 2.5 , Spring 4.2.4
Database : Redis Jedis 2.7.2 
Test: Junit 4.12

2. How to Launch Apps 
Method 1:
  Environment Requirement: 
    1.Redis installed and service on port 6379.
    (You Redis server IP and port can be changed on the path /shortenurl-web/src/main/resources/conf/resource.properties)
    2.Java 8 and Maven installed
    3.Tomcat server installed
  Process:
    1.Start Redis service. (My default is 192.168.25.130:6379).
    2.Deploy the war package on tomcat and set port 9000.
    3.Access the index page (localhost:9000) on browser. 
    4.Enter the long URL that you want to be shortened. 
    5.Copy the shorten url to the browser and you can be 	redirected to the original url.

Method 2:
  Environment Requirement: 
    1.Redis installed and service on port 6379. 
    2.Java 8 and Maven installed
  Process:
    1.Start Redis service. (My default is 192.168.25.130:6379).
    2.Open this project on your own IDE. Run maven build with “clean tomcat7:run” ( I installed a tomcat plug-in and assign on port 9000.       So you don’t have to have a tomcat server).
    3.Access the index page (localhost:9000) on browser. 
    4.Enter the long URL that you want to be shortened. 
    5.Copy the shorten url to the browser and you can be redirected to the original url.
    
3. Workflow:
  1.Designed several Javascript functions to provide hints on UI JSP until user enter the valid URL. 
  2.Configure Spring container, set up Redis server and initialize Redis connection pool instance in containers.
  3.Design Java Redis client interfaces and implementations.
  4.Write several test cases to check the database connection methods needed in this project.
  5.Design web controller to handle request with longURL parameter using SpringMVC. Store the mapping relationship in Redis. Using the       Redis incr function to generate shortened ID. Designed get short url and store mapping relationship handler. 
    Design redirected handler. Get the short URL and query database to get and redirect request to 	original URL.
    (I do not set up the key expire time. I assume short url does not 	expire.)
