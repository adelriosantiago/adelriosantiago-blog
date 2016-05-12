<permalink>eng</permalink>
<month>9</month>
<year>2015</year>

# How to deploy websites on your server with Dropbox

Deploying websites with Dropbox is really cool! I've found that this is one of the fastest ways to instantly deploy websites on your server. But before I jump in and explain the benefits and how you can implement that on your own server, let me be clear about this: Dropbox is not exactly the safest tool out there...

Dropbox's security standards are actually high. What makes it insecure is how easy is to make changes to the files, someone with access to your computer could easily create, copy or delete files or folders. If you lose access to your mail associated with it, personal information could end up in wrong hands. By far what makes Dropbox insecure is how easy is to forget to whom you shared an specific folder. If you use Dropbox on a daily basis I bet that there is at least one folder that is shared with a person that shouldn't be there... I once conducted a rather quick and informal poll/test and found that 3 out of 5 people using Dropbox for at least 1 year would end up kicking a person from a folder after I asked them to review their shared folders. You still don't believe me? Go ahead to Dropbox > Sharing to have a "Whaaat! Is he/she still invited to this folder???" moment.

On the other hand, deploying several times a day is essential for startups (see Lean's **continuous integration** & **continuos delivery** concepts). I found this quote about CI:

*"Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily."*

And this one about CD:

*"Continuous Delivery is the natural extension of Continuous Integration: an approach in which teams ensure that every change to the system is releasable, and that we can release any version at the push of a button."*

Both quotes from Martin Fowler @ [ThoughtWorks](https://www.thoughtworks.com/continuous-delivery)

Bear in mind that by using Dropbox you are losing the chances to resolve conflicts like in GIT, so far Dropbox only creates a conflicted copy of your work that you will have to merge manually or with a merging tool. ~~Also, bear in mind that with Dropbox there is no way to go back in history. **Once you lose a file version, its gone, forever**.~~ A very nice feature that seems to be added recently allows you to go back in history!

<hidden>It seems that Dropbox now creates conflict copies.</hidden>

Here are the steps to achieve that:

<hidden>TODO: add some images here?</hidden>

 - Download Dropbox on your local machine -_-
 - Download the Dropbox daemon on your linux machine as explained on [this article](https://www.dropbox.com/install?os=lnx). If you need to know if you are running a 32 or 64 bits machine just type `uname -a`, a 32 bits machine withh throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 While a 64 bits machine will throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
 - Now run the Dropbox daemon with `~/.dropbox-dist/dropboxd &`, this should create a folder named "Dropbox" on $HOME.
 - To link your Apache folder to the actual Dropbox folder create a soft link from /var/www/html/yoursite to $HOME/Dropbox/yoursite.
 
 
Now you can collaboratively edit your websites with your favorite IDE! Try creating a file named index.html in your local machine, add some content on it and test it on the real www address.

<hidden>Also, check this article that I wrote: [I need to write this... and put the link here] about how to setup your own Dropbox, just in case you don't want to use it.</hidden>

---
<hidden>
alternative title:
# How to sync your Digital Ocean instance with Dropbox

some excerpts:

So that created this soft link: ln -s /var/www/html/lumston ./website

One of the fastest ways to sync your local changes and a real server is using Dropbox. 

Una de las maneras mas eficientes que hay para sincronizar una pagina web con tu projecto local es Dropbox. 

I recently tried to use Dropbox to sync one of my projects on my Digital Ocean instance. 


Pasos para sync de Dropbox
•	bajar dropbox en la computadora desktop
•	saber si es 32 bits o 64 bits la instancia de DO
o	uname –a
o	32  bits: Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
o	Another 32 bits: Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i686 GNU/Linux
o	64 bits:  Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
•	Install the script from https://www.dropbox.com/install?os=lnx
•	Run the deamon with ~/.dropbox-dist/dropboxd & (segun yo si se reuqiere el &) 
•	Create a link from /var/www/html/yoursite to $HOME/Dropbox/yoursite, the index.html path is /var/www/html/yoursite/index.html
•	For example the index.html file of the site I wanted to sync is at /var/www/html/site/index.html, therefore I created the following link to the $HOME/Dropbox folder:
ln –s 



--- trash (didn't like these excerpts at the end)
The Dropbox's security standard is actually high, what makes it insecure is how easy is to change files if some else steals your mail associated with Dropbox , how easy it is for the people to mismanage the collaborators and of course, how easy is to forget about who you shared with your Dropbox folder.
I've found that one of the fastest ways to instantly deploy websites is to use Dropbox on your server. For sure you have used Dropbox or at least know how it works. It basically allows you to keep all your files sync'ed.

One of the most time consuming tasks while deploying a server is when you have to deploy your localhost changes into the real server and have to login to it and just do a `git pull`. If you are building a simple website, pure html, with no connections to databases and transactions you should try using Dropbox as your deploy tool.


Now let me be clear about two things: 
 - It is very well know that Dropbox is not exactly the safest tool out there... You should use **only** when the security is not a key factor (like when doing a landing page).
 - Also, Dropbox is not a "version control system" and it doesn't do anything to mitigate overwrite conflicts like GIT.

 Also I think it using Dropbox as your version control system would look very unprofesional... Aside from that, if you are just rocking your startup, what are you waiting to use Dropbox as your deploy tool!?
 
</hidden>

<hidden>If you are building a simple website or landing page, pure html, with no connections to databases and/or transactions to other services. On these situations, deploying websites with the professional tools like GIT, Mercurial and SVN is one of the most time-consuming tasks as you have literally have to login into the server just to do a `git pull`.</hidden>