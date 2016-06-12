<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# How to deploy websites on your server with Dropbox

<hidden>TODO: add some images here?</hidden>

 - Download Dropbox on your local machine -_-
 - Download the Dropbox daemon on your linux machine as explained on [this article](https://www.dropbox.com/install?os=lnx). If you need to know if you are running a 32 or 64 bits machine just type `uname -a`, a 32 bits machine withh throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
 While a 64 bits machine will throw something like:
 Linux discworld 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux 
 - Now run the Dropbox daemon with `~/.dropbox-dist/dropboxd &`, this should create a folder named "Dropbox" on $HOME.
 - Finally, to link your Apache folder to the actual Dropbox folder create a soft-link from /var/www/html/yoursite to $HOME/Dropbox/yoursite.

<hidden>fast drafting</hidden>

<hidden>themes & ideas</hidden>

