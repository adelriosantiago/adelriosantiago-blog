<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# How to secure your MongoDB installation

MongoDB is often associated with poor security database deploys, I think the main reason for this is very simple: By default MongoDB requieres no password to authenticate. This simple fact makes it one of the most [probable to misuse] database frameworks out there. Programers, under the pressure to deplot the project usually give little or no importance to securing their DB's. Also MongoDB University makes (IMHO) a big mistake not including this specific subject on their courses. I think it is until the third tutorial when this subjectº is addressed


---

Here is a small checklist to secure your MongoDB instance:

1.- If you are using a MongoDB versions lower than 2.6 then *you need* and really mean *you need* to disable external access to the database, this will make your DB accessible only from your localhost. This is done by opening the file "mongod.conf" and adding the line "bind_ip = 127.0.0.1" to it. Replace if it already exists. MongoDB added this setting by default on versions 2.6.

1.1.- (Optional) As you can see on the mongod.conf file there is the "port" value, you can also change it if you don't want to use the default port, howeever I don't recommend this, if a hacker is good enough he will very likely use a port scanner anyway./nothing prevents a hacker to use a port scanner./a good hacker would use a port scanner anyway.

2.- Disable incoming connections to port 27017
You just disabled external connections on steo 1 but you should anyway block access to the port (just in case). The UFW (or Uncomplicated Firewall) is a very useful, easy-to-use firewall for Linux. Chances are that your linux distro already have this package installed by default. In case you don't, install it with `sudo apt-get install ufw` and then do a `sudo ufw status verbose` to get the firewall current status.

3.- Disable HTTP interface: Apparently MongoDB has a HTTP interface running on port 27018, quite frankly I have never seen it working quite frankly but you should disable it. Editing the mongod.conf to
`nohttpinterface = true`

It is better to completely disable incoming connections to your database. I do this by doing,

`sudo ufw allow ssh` #If you are connecting through SSH (like AWS EC2 or Digital Ocean) you need to enable this, otherwise you will immediately lose connection to your Ubuntu instance after enabling the firewall.
`sudo ufw allow <port>` #Replace <port> with any port that you want to be accessed. I allow only 80 (HTTP) and port 3000 where another Node.JS app is running.

Warning: By default all ports are disabled when enabling UFW. Make sure that ssh is enabled if you are currently connected this way.

`sudo ufw enable` #Enable UFW
``
``
``

This will disable external connections to the database. You will, of course, be unable to make queries to the database from your app. I really recommend that you create a webservice or API for your app and make the needed calls through that. If you don't want to do that then you can [enable port 27017 only to a single ip] with the command `sudo ufw allow from <target> to <destination> port <port number>` for example `sudo ufw allow from 192.168.0.4 to any port 27017` would allow access from the ip 192.168.0.4; bear in mind that you will need to have a static IP or your service will stop working as soon as a new IP is obtained.

Tips for AWS EC2 users: Instances have it's own firewall, it is called Security Groups inside your Management Console. Also

3.-


Resources:
[https://docs.mongodb.org/manual/administration/security/#SecurityandAuthentication-FirewallRules]
[http://stackoverflow.com/questions/20459479/default-mongodb-connection-safety]
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