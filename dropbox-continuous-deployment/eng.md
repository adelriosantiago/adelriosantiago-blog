<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# Deploying websites with Dropbox

Deploying your code several times a day is essential for tech startups (see Lean's **continuous integration** & **continuos delivery** concepts). I have found this excerpt that explains CI very well:

*"Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily."*

Quote from Martin Fowler @ [ThoughtWorks](https://www.thoughtworks.com/continuous-delivery)

There are several professional tools to implement CI. Tools like Jenkins and Travis allow you to do that. Or you can also follow this [tutorial on how to do implement your own basic CI with GIT hooks](http://https://www.digitalocean.com/community/tutorials/how-to-use-git-hooks-to-automate-development-and-deployment-tasks). If you want to try an out-of-the-box tool, try Dropbox, a tool that although not meant to be a professional CI/CD tool, is both easy to install and powerful.

<hidden>TODO: add some images here?</hidden>

Here are the steps to start deploying websites with Dropbox:

 - Download Dropbox on your local machine *(-_- nuff said)*.
 - Download the Dropbox daemon on your linux machine as explained on [this article](https://www.dropbox.com/install?os=lnx). If you need to know if you are running a 32 or 64 bits machine just type `uname -a`, a 32 bits machine withh throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 While a 64 bits machine will throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
 - Now run the Dropbox daemon with `~/.dropbox-dist/dropboxd &`, this should create a folder named "Dropbox" on $HOME.
 - Finally, to link your Apache folder to the actual Dropbox folder create a soft-link from /var/www/html/yoursite to $HOME/Dropbox/yoursite.

Now you can invite your team and start developing websites together.
 
<hidden>fast drafting</hidden>

<hidden>themes & ideas</hidden>

