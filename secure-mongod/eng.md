<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# How to secure your MongoDB installation

MongoDB is often associated with poor security database deploys, I think the main reason for this is very simple: By default MongoDB requieres no password to authenticate. This simple fact makes it one of the most [probable to misuse] database frameworks out there. Programers, under the pressure to deplot the project usually give little or no importance to securing their DB's. Also MongoDB University makes (IMHO) a big mistake not including this specific subject on their courses. I think it is until the third tutorial when this subjectº is addressed


---

Here is a small checklist to secure your MongoDB instance:

1.- Disable port 27017 via de UFW firewall
The UFW (or Uncomplicated Firewall) is a very useful, easy-to-use firewall for Linux. Your linux distro may already have this package installed by default. In case you don't, install it with `sudo apt-get install ufw` and then do a `sudo ufw status verbose` to get the firewall current status.

The thougher security

I usually block the port 27017 (the default MongoDB port) with:

You can block any access to the port 27017 with `sudo ufw `


Mongo offers only very basic security (quote)

I find it funny how difficult is to find tutorials to secure your Mongo deploy.

A group of students who found nearly 40,000 databases without any kind of security, some of them containing sensitive information.
This article/study [http://www.securityweek.com/thousands-mongodb-databases-found-exposed-internet] conducted a ethical hack and found that [5000 databases without password] some of them including sensite information.

There is no excuse! Secure your MongoDB deploy now!