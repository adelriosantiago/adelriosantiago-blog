<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# How to secure your MongoDB installation

MongoDB is often associated with poor security database deploys, I think the main reason for this is very simple: By default MongoDB requieres no password to authenticate. This simple fact makes it one of the most [probable to misuse] database frameworks out there. Programers, under the pressure to deplot the project usually give little or no importance to securing their DB's. Also MongoDB University makes (IMHO) a big mistake not including this specific subject on their courses. I think it is until the third tutorial when this subjectº is addressed


---

Here is a small checklist to secure your MongoDB instance:

1.- Disable incoming connections to port 27017
The UFW (or Uncomplicated Firewall) is a very useful, easy-to-use firewall for Linux. Chances are that your linux distro already have this package installed by default. In case you don't, install it with `sudo apt-get install ufw` and then do a `sudo ufw status verbose` to get the firewall current status.

It is better to completely disable incoming connections to your database. I do this by doing,

`sudo ufw allow ssh` #If you are connecting through SSH (like AWS EC2 or Digital Ocean) you need to enable this, otherwise you will immediately lose connection to your Ubuntu instance after enabling the firewall.
`sudo ufw allow [port]` #Replace [port] with any port that you want to be accessed. I allow only 80 (HTTP) and port 3000 where a Node app is running.
`sudo ufw enable` #Enable UFW
``

This will disable external connections to the database. You will -of course- be unable to make queries to the database from your app. I really recommend that you create a webservice or API for your app and make the needed calls through that. If you don't want to do that then you can [enable port 27017 only to a single ip]

[http://stackoverflow.com/questions/20459479/default-mongodb-connection-safety]
[https://www.digitalocean.com/community/questions/how-to-do-mongodb-backups-and-enhance-security]
[https://www.digitalocean.com/community/tutorials/how-to-securely-configure-a-production-mongodb-server]
[http://blog.mongodirector.com/10-tips-to-improve-your-mongodb-security/]
[http://serverfault.com/questions/237762/how-to-make-a-secure-mongodb-server]
[http://serverfault.com/questions/237762/how-to-make-a-secure-mongodb-server]
[https://www.digitalocean.com/community/tutorials/how-to-setup-a-firewall-with-ufw-on-an-ubuntu-and-debian-cloud-server]
[]
[]


I usually block the port 27017 (the default MongoDB port) with:

You can block any access to the port 27017 with `sudo ufw `


Mongo offers only very basic security (quote)

I find it funny how difficult is to find tutorials to secure your Mongo deploy.

A group of students who found nearly 40,000 databases without any kind of security, some of them containing sensitive information.
This article/study [http://www.securityweek.com/thousands-mongodb-databases-found-exposed-internet] conducted a ethical hack and found that [5000 databases without password] some of them including sensite information.

There is no excuse! Secure your MongoDB deploy now!