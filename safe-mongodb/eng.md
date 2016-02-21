<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# How to secure your MongoDB instance

MongoDB is often associated with poor security database deployments, I think the main reason for this is very simple: By default MongoDB requieres no password to authenticate. This simple fact makes it one of the most [probable to misuse] database frameworks out there. Programers, under the pressure to deplot the project usually give little or no importance to securing their DB's. Also MongoDB University makes (IMHO) a big mistake not including this specific subject on their courses. I think it is until the third tutorial when this subjectº is addressed

---

MongoDB offers only basic security.
I find it funny that the security is not very well documented as other parts of documentation are. I suppose this is because Mongo is still relatively young, security is somethings that grows along with any project.

Here is a small checklist to secure your MongoDB instance:

1.- If you are using a MongoDB versions lower than 2.6 then *you need* and really mean *you need* to disable external access to the database, this will make your DB accessible only from your localhost. This is done by opening the file "mongod.conf" and adding the line "bind_ip = 127.0.0.1" to it. Replace if it already exists. MongoDB added this setting by default on versions 2.6. Also, please consider migrating to version 3.0 or later as it includes several security improvements.

2.- (Optional) On the next line on the same file. You can see the "port" value, you can also change it if you don't want to use the default port, however I don't recommend this, I consider it a lame obfuscation attempt, I've seen programmers attempting to "secure" therir DB deployments just by changing the default port. This is a bad idea and in any case you should worry only about hackers that know how to perform a port scan./Bear in mind that if a hacker is good enough he will very likely use a port scanner anyway./nothing prevents a hacker to use a port scanner./a good hacker would use a port scanner anyway.

3.- Disable incoming connections to port 27017
You just disabled external connections on steo 1 but you should anyway block access to the port (just in case). The UFW (or Uncomplicated Firewall) is a very useful, easy-to-use firewall for Linux. Chances are that your linux distro already have this package installed by default. In case you don't, install it with `sudo apt-get install ufw` and then do a `sudo ufw status verbose` to get the firewall current status. Your `sudo ufw status verbose` should look like:

()[images/ufw.png]

4.- Disable HTTP interface: Apparently MongoDB has a HTTP interface running on port 27018, quite frankly I have never seen it working but you should disable it when going into production. Uncomment or add `nohttpinterface = true` the mongod.conf.

5.- Always run mongo with authentication: This is done by running `mongod --auth`. This way you will be prompted your username and password when connecting. Here are are the stummarized steps taken from the article (Enable Client Access Control)[https://docs.mongodb.org/v3.0/tutorial/enable-authentication/]

6.1.- Run `mongod` to run the daemon without access control.
6.2.- Connect to the instance with `mongo` on another terminal
6.3.- Create a database administrator user with `db.createUser({user: "exampleAdminUser", pwd: "exampleAdminPass", roles: [{role: "root", db: "admin"}]})`. This is the admin username, don't change the field *db* yet. Also note that while the documentation states that you should create the admin user with "userAdminAnyDatabase", (this setting don't seem to work for many people)[http://stackoverflow.com/questions/23943651/mongodb-admin-user-not-authorized].
6.4.- Close all mongo and mongod terminals.
6.5.- Run `mongo -u "exampleAdminUser" -p "exampleAdminPass" --authenticationDatabase "admin"` to run the daemon with access control.
6.6.- Create a database user with `use exampleDatabase db.createUser({user: "exampleUser", pwd: "examplePass", roles: [{role: "readWrite", db: "exampleDatabase"}]})`
6.7.- Finally connect to exampleDatabase with this user, like `mongo -u "exampleUser" -p "examplePass" --authenticationDatabase "exampleDatabase"`

You now have two users to remember and document on your password reminder page:
You now have two users to register on your password notebook. (If you don't have a password notebook you should)[link]:

 - The database administrator account "exampleAdminUser", this user can manage every single database on the MongoDB instance.
 - The "exampleUser" account, this will have read/write permissions only on the database "exampleDatabase".
 
 

---

4.- Add a user to the Admin database and connect trghoug it:

`db.createUser({user: "exampleUser", pwd: "examplePass", roles: [{role: "userAdminAnyDatabase", db: "admin"}]})`
Other available permissions/roles are `role: "read"` and role: "write". Don't replace the "admin" database with your database you want to manage, you will add a user for that later.

Start mongod with authentication enabled `mongod --auth`

Connect to your mongo instance with the command `mongo -u "exampleUser" -p "examplePass" --authenticationDatabase "admin"`.

This is the the admin user, now create a user for a single database:

[create a single user for "exampleDatabase"]

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
[https://docs.mongodb.org/v3.0/tutorial/enable-authentication/]
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