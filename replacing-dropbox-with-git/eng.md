<permalink>eng</permalink>
<month>3</month>
<year>2020</year>

# Deploying websites in *almost*-real-time with GIT

Long long time ago I wrote about [how to deploy websites using Dropbox](http://adelriosantiago.com/gitblog/eng/dropbox-continuous-deployment) in order to release website changes multiples times a day. I recently decided to create my own cheap-Dropbox alternative that allows me to do so without depending on a third party. It is called [git-as-dropbox](https://www.npmjs.com/package/git-as-dropbox) and is extremely simple to use. Just `git-as-dropbox [your_repo]` and it will begin syncing your repositories in *almost*-real-time.