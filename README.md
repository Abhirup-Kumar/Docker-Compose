# Docker-Compose
Project on docker compose. Integrating MySql with Joomla while both running on separate docker O.S. 

"Beginner to Expert Level" was the title of the video I started watching on Docker. I was a beginner , just started docker with that only but now I can say that now I not only know Docker but actually pretty confident in it as well.
It was an instructor-led live session by Mr Vimal Daga who helped me reach this stage under his IIEC-1.0 campaign.
Here I share you my work and project on Docker:

Description

This is a project which checks the practical knowledge of Docker and Docker-Compose.
We started with mysql and joomla. Setting up both and then integrating with each other. This system of using multiple O.S. or independent systems  tied together is termed as Multi-tier architecture. Hence here we achieve multi-tier architecture. Using the concepts of PAT , persistent storage as well.

MULTI-TIER ARCHITECTURE ON DOCKER  
Using docker-compose to code the whole architecture.
MySql and Joomla were linked together.

TOOLS / PRODUCTS USED:
VMware or VirtualBox. 
Linux O.S. (used REDHAT here).
MySql and Joomla container image.
Clear Concepts of Networking (iptables, port forwarding).
Clear Concepts of Volumes and storage.
Client Web-browser.
Docker-Compose.

About MySQL
MySQL is the world's most popular open source database. With its proven performance, reliability and ease-of-use, MySQL has become the leading database choice for web-based applications, used by high profile web properties including Facebook, Twitter, YouTube, Yahoo! and many more.

About Joomla
Joomla is an open source platform on which Web sites and applications can be created. It is a content management system (CMS) which connects your site to a MySQLi, MySQL, or PostgreSQL database in order to make content management and delivery easier on both the site manager and visitor.
Joomla's primary focus has been on usability and extensibility since its initial release in 2005. It is because of this that the project has been the recipient of numerous awards, including being a three-time recipient of the PACKT Open Source Content Management System Award.
Joomla is a completely free open source solution available to anyone and everyone with a desire to build dynamic and robust sites for a variety of purposes. Joomla has been utilized by some of the Web's most recognizable brands including Harvard, iHop, and MTV. It is capable of carrying out tasks ranging from corporate websites and blogs to social networks and e-commerce.

Prior-Settings:
After setting up the Linux O.S. and an active internet connection is an absolute prerequisite. 
After we basics setup, now begin installing. Download docker-ce and install on the base O.S. Then download the container images of MySQL and Joomla.

Some tweaks:
Some changes are required in the system to let the infrastructure work smoothly. First we disable firewall and allow all packets in iptables. Now I know it is not safe to do both of these steps but as a beginner my focus  was mainly on setting up the docker infrastructure and didn't give much to security. For now, we can go along with this and when we finish this up we can do some tweaks in this security domain as well.

For firewall:
`systemctl stop firewalld`
`systemctl disable firewalld`

First command to just disable firewall but through 2nd command we permanently turn it off so that after O.S. resarts,  it doesn't get active again.

For iptables:
`iptables -F` 
`iptables -nvL`
`iptables -P FORWARD ACCEPT`
`Iptables -nvL`

First command to flush all rules which were already set-up. 2nd to check the results for the 1st command. 3rd command to make changes in iptable and allow all traffic. Again 4th command to check the results.

Begin Core:

Now that the setting up is done, lets begin with the core of the project.

To download the docker-ce:

`yum install docker-ce`

If some minor hiccups then:

`yum install docker-ce --nobest`

Then let's start these services:

`systemctl start docker`
`systemctl enable docker`

This concludes the installing and running the docker engine. If any problems persist in installation then some changes might be required in repo files, you can contact me if the problem is still there.

Now we pull container images of MYSQL and Joomla:

First make your account on https://hub.docker.com/ so that you can pull and push images with ease. Mainly an account is required if you want to push.

`docker pull mysql:5.7`

Form the website: https://hub.docker.com/_/mysql

Then...

`docker pull joomla`

From the website : https://hub.docker.com/_/joomla

Yes, I have downloaded version 5.7 of MySQL for just some compatibility reasons.

Setup MySQL at both ends

At both ends here means at both client and server side. MySQL working at the server side needs the client side so that we can connect to it as well.

At Server Side:
‘docker run -it -e MYSQL_ROOT_PASSWORD= your_password -e MYSQL_USER=your_user name -e MYSQL_PASSWORD=user_password -e MYSQL_DATABASE=database name --name joomladb mysql:5.7`

This code will use mysql image to launch mysql server which we will connect to, for that we need its IPAddress , for this we do: 
`docker inspect container_id | grep IP`

Suppose IP is `172.18.0.2`

This will bring the ip address , note it down.

At client side (Base O.S.)
`yum install mysql`

After installation we need to connect to it , for this:
`mysql -h 172.18.0.2 -u username -ppassword`

Remember : NOT TO GIVE SPACE BETWEEN -p AND password.

Through this we now know how to set up mysql at both server and client side.

P.S. - Working with joomla is easy so we will directly configure it in docker-compose file.  


DOCKER COMPOSE

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration. 
Define the services that make up your app in docker-compose.yml so they can be run together in an isolated environment.
Run docker-compose up and Compose starts and runs your entire app.

Docker compose can be downloaded and installed here: https://docs.docker.com/compose/install/
Once you install docker compose , go inside the specified directory.
This is a standard directory so that you don't have to specify file path while launching docker compose.

`cd /mycompose`
`vim docker-compose.yml`
And also it has to be in yml format as this is the format that docker compose take as a file for instructions.

FIRING IT UP!!
Now since all have been set it time to start our docker-compose and set up the desired infrastructure with this single piece of file of code.
It is started with:
`docker-compose up`

RESULTS:
To check its actual results we now test it working. For this, we go to client browser , type the IP of Joomla container which you can find by doing : `docker inspect docker_id | grep IP` . enter this in search bar of browser and if you see the home page of Joomla like the picture below:

DOWN!!
Now if we want to terminate the whole infrastructure we can use 
`docker-compose down`
This will bring down the whole setup and if you want it to rev it up again, you can use `docker-compose up` again and it’s running again.






References:

https://www.mysql.com/about/

https://hub.docker.com/_/mysql

https://hub.docker.com/_/joomla

https://rockettheme.com/docs/joomla/platform


