<permalink>eng</permalink>
<month>9</month>
<year>2015</year>

# How to sync your Digital Ocean instance with Dropbox

One of the fastest ways to instantly deploy websites is to use Dropbox on your server. For sure you have used Dropbox or at least know how it works. It basically allows you to keep all your files sync'ed. 

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



