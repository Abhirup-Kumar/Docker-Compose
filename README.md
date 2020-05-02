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
Systemctl stop firewalld
Systemctl disable firewalld

First command to just disable firewall but through 2nd command we permanently turn it off so that after O.S. resarts,  it doesn't get active again.

For iptables:
`iptables -F` 
`iptables -nvL`
`iptables -P FORWARD ACCEPT`
`Iptables -nvL`

First command to flush all rules which were already set-up. 2nd to check the results for the 1st command. 3rd command to make changes in iptable and allowing all traffic. Again 4th command to check the results.

Begin Core:

Now that's the setting up is done, lets begin with the core of the project.







References:

https://www.mysql.com/about/

https://hub.docker.com/_/mysql

https://hub.docker.com/_/joomla

https://rockettheme.com/docs/joomla/platform


