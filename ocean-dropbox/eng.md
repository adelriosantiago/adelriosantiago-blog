<permalink>eng</permalink>
<month>9</month>
<year>2015</year>

# How to deploy websites on your server with Dropbox

Deploying your code several times a day is essential for tech startups (see Lean's **continuous integration** & **continuos delivery** concepts). I found this excerpt that explains CI very well:

*"Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily."*

Quote from Martin Fowler @ [ThoughtWorks](https://www.thoughtworks.com/continuous-delivery)

There are several professional tools to implement CI. Tools like Jenkins and Travis allow you to do that. Or you can also follow this [tutorial on how to do implement your own basic CI with GIT hooks](http://https://www.digitalocean.com/community/tutorials/how-to-use-git-hooks-to-automate-development-and-deployment-tasks). If you want to try something different, try Dropbox.

Deploying websites with Dropbox is really cool! I've found that this is one of the fastest ways to instantly deploy websites on your server. But before I jump in and explain the benefits and how you can implement that on your own server, let me be clear about this: Deploying your code with Dropbox is not exactly the best/safest thing to do.

It is not about Dropbox's security standards, which are actually high. What makes it insecure is how easy is to make changes to the files. Someone with access to your computer could easily create, copy or delete files or folders. If you lose access to your mail associated with it, personal information could end up in wrong hands. By far what makes Dropbox insecure is how easy is to forget to whom you shared an specific folder. If you use Dropbox on a daily basis I bet that there is at least one folder that is shared with a person that shouldn't be there... I once conducted a rather quick and informal poll/test and found that 3 out of 5 people using Dropbox for at least 1 year would end up kicking a person from a folder after I asked them to review their shared folders. If you are Dropbox user then go to the Dropbox > Sharing tab to have a "Whaaat! Is he/she still invited to this folder???" moment. 

Bear in mind that by using Dropbox you are losing the chances to resolve conflicts like in GIT, so far Dropbox only creates a conflicted copy of your work that you will have to merge manually or with a merging tool. ~~Also, bear in mind that with Dropbox there is no way to go back in history. **Once you lose a file version, its gone, forever**.~~ A very nice feature that seems to be added recently allows you to go back in history!

<hidden>TODO: add image here, already on the folder</hidden>

Having all that in mind, if you are ready to see hundreds *-or maybe thousands-* of deploys per day (I see about 800 on a small sized dev team) here are the steps to implement Dropbox on your server:

<hidden>TODO: add some images here?</hidden>

 - Download Dropbox on your local machine -_-
 - Download the Dropbox daemon on your linux machine as explained on [this article](https://www.dropbox.com/install?os=lnx). If you need to know if you are running a 32 or 64 bits machine just type `uname -a`, a 32 bits machine withh throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 While a 64 bits machine will throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
 - Now run the Dropbox daemon with `~/.dropbox-dist/dropboxd &`, this should create a folder named "Dropbox" on $HOME.
 - Finally, to link your Apache folder to the actual Dropbox folder create a soft-link from /var/www/html/yoursite to $HOME/Dropbox/yoursite.

<hidden>TODO: add the soft-link example ln –s</hidden>

Now you can collaboratively edit your websites with your favorite IDE! Try creating a file named *index.html* in your local machine, add some content on it and test it on the real *www* address.

<hidden>Also, check this article that I wrote: [I need to write this... and put the link here] about how to setup your own Dropbox, just in case you don't want to use it.</hidden>

<hidden>If you are building a simple website or landing page, pure html, with no connections to databases and/or transactions to other services. On these situations, deploying websites with the professional tools like GIT, Mercurial and SVN is one of the most time-consuming tasks as you have literally have to login into the server just to do a `git pull`.</hidden>