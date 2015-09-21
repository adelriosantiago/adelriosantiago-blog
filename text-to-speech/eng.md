<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# SVOX TTS (Text to Speech) interface in Node.js

Google has a very cool service to convert text to audio via the Google Translate engine. You can easily test it going to the [service webpage](http://translate.google.com), and clicking on the <a class='mintip'>megaphone icon<span><img src='../articles/images/google-tts.png'/></span></a> to read the text aloud. <a class='mintip'>Inspecting the button with the browser toolbar<span><img src='../articles/images/behind-scenes.png'/></span></a> we find how it works. Behind the scenes when you click on it there is a call to an address with the text we want to read aloud, so that when you click on the megaphone you are actually performing a requests like these:

 * [translate.google.com/translate_tts?tl=en&q=hello-world](http://translate.google.com/translate_tts?tl=en&q=hello-world) to read “hello world” in english.
 * [translate.google.com/translate_tts?tl=it&q=buongiorno](http://translate.google.com/translate_tts?tl=it&q=buongiorno) to read aloud “buongiorno” in italian.

And so on with other languages.

However there is a big issue with service. It is the usual story of free services and APIs: *The service was free, people abused from it, it became a paid service...* Google now puts a limit the quantity on audios you can generate to about 15 calls per user (unless the call is made from Chrome), after that limit is reached you will very likely get an <a class='mintip'>unusual traffic<span><img src='../articles/images/deny-tts-google.png'/></span></a> captcha making the service unusable for your app. In order to raise the limit again you would need to solve the captcha. As a student, I once had a situation like this on a project with an Arduino MCU.

> "Ohh wait teacher! The project is workin' just lemme answer this captcha to prove that I’m not a robot!”
> -☉_☉

With this project you will be able to set-up your own Text to Speech server for your apps using the [SVOX package](https://launchpad.net/ubuntu/+source/svox) engine in Ubuntu. **Bear in mind that the SVOX speech synthesis quality is far lower than Google's engine.** The voices simply don't sound very natural. On the bright side, you can flood your Ubuntu server with thousand calls if needed!

Some project ideas that could use this web interface are:
 * A speaking Arduino that talks when you press some buttons.
 * An accessibility app for the blind. Maybe an Android app that reads Barcodes aloud *(there are some good tutorials about [how to read barcodes](http://code.tutsplus.com/tutorials/android-sdk-create-a-barcode-reader--mobile-17162) and [how to read barcodes and QR codes](http://examples.javacodegeeks.com/android/android-barcode-and-qr-scanner-example/))*
 * A computer clock that reads the time every hour (like on Mac).

Find the project and the installation instructions at the Github repo [https://github.com/adelriosantiago/svox-interface-nodejs](https://github.com/adelriosantiago/svox-interface-nodejs). You will need a Virtual Machine running Ubuntu or a server (AWS and Digital Ocean are both very good) instance in order to get the SVOX TTS engine running. Also you will need [Node.js](http://nodejs.org) to create the web request interface.

Here is how the finished project looks like:

<a href='http://tts.adelriosantiago.com'>![](../articles/images/tts-final.png)</a>

To use simply select the language, the text you wish to convert and click on the URL to get the audio. Feel free to play with the finished project generating some phrases at the address [tts.adelriosantiago.com](http://tts.adelriosantiago.com).


