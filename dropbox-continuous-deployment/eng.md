<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# Deploying websites with Dropbox

Deploying your code several times a day is essential for tech startups (see Lean's **continuous integration** & **continuos delivery** concepts). I have found this excerpt that explains CI very well:

*"Continuous Integration is a software development practice where members of a team integrate their work frequently, usually each person integrates at least daily."*

Quote from Martin Fowler @ [ThoughtWorks](https://www.thoughtworks.com/continuous-delivery)

<hidden>TODO: add some quote images here?</hidden>
<hidden>TODO: add workflow image here</hidden>

There are several professional tools to implement CI. Tools like Jenkins and Travis allow you to do that. Or you can also follow this [tutorial on how to do implement your own basic CI with GIT hooks](http://https://www.digitalocean.com/community/tutorials/how-to-use-git-hooks-to-automate-development-and-deployment-tasks). If you want to try an out-of-the-box tool, try Dropbox, a tool that although not meant to be a professional CI/CD tool, is both easy-to-install and powerful.

<hidden>TODO: add some images here?</hidden>

Here are the steps to start deploying websites with Dropbox:

 - Download Dropbox on your local machine *(-_- nuff said)*.
 - Download the Dropbox daemon on your linux machine as explained on [this article](https://www.dropbox.com/install?os=lnx). If you need to know if you are running a 32 or 64 bits machine just type `uname -a`, a 32 bits machine withh throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 While a 64 bits machine will throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
 - Now run the Dropbox daemon with `~/.dropbox-dist/dropboxd &`, this should create a folder named "Dropbox" on $HOME.
 - You will be asked to visit a link on your browser.
```
This computer isn't linked to any Dropbox account...

Please visit https://www.dropbox.com/cli_link_nonce?nonce=[code] to link this device.
```
 - Finally create a soft-link shortcut between your Apache folder and the actual Dropbox folder, so that the content is mirrored between /var/www/html/yoursite and $HOME/Dropbox/yoursite.

Now you can invite your team and start developing websites together.

Bear in mind that by using Dropbox you are losing the chances to resolve conflicts like in GIT, so far Dropbox only creates a conflicted copy of your work that you will have to merge manually or with a merging tool. ~~Also, bear in mind that with Dropbox there is no way to go back in history. **Once you lose a file version, its gone, forever**.~~ A very nice feature that seems to be added recently allows you to go back in history, but still, bear in mind that *Dropbox is not a replacement of GIT*.

Also note that someone with access to your computer could easily create, copy or delete files or folders on your server. Even more, if you lose access to your mail associated with it, personal information could end up in wrong hands. I have noticed that by far what makes Dropbox not a *very safe tool* is how easy it is to forget to remove users that you have previously shared access with.

If you use Dropbox on a daily basis I bet that there is at least one folder that is shared with a person that shouldn't be there... I once conducted a small quick and informal poll/test and found that **3 out of 5 people using Dropbox for at least 1 year would ended up kicking a person from a shared folder after I asked them to review their folder settings**. Go to your shared folders now and find out if you are one of them.

Still, Dropbox as a CI tool is very powerful and useful, if you have an early startup give it a try!
 
<hidden>fast drafting</hidden>

<hidden>themes & ideas</hidden>

