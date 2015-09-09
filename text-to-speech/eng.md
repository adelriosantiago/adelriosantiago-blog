<permalink>eng</permalink>
<month>8</month>
<year>2015</year>

# SVOX TTS (Text to Speech) interface in Node.js

As you probably know, Google has a service to convert text to audio via the Google Translate engine. You can easily test it by clicking on the <a class='mintip'>megaphone icon<span><img src='../articles/images/google-tts.png'/></span></a> to read the text aloud. <a class='mintip'>Inspecting the button with the browser toolbar<span><img src='../articles/images/behind-scenes.png'/></span></a> we find that what is actually going on behind the scenes is a call to an address with the text we want to read aloud, so that when you click on the megaphone you are actually performing a requests like these:

 * [translate.google.com/translate_tts?tl=en&q=hello-world](http://translate.google.com/translate_tts?tl=en&q=hello-world) to read “hello world” in english.
 * [translate.google.com/translate_tts?tl=it&q=buongiorno](http://translate.google.com/translate_tts?tl=it&q=buongiorno) to read aloud “buongiorno” in italian.

And so on with other languages.

Now imagine yourself creating and Android or Arduino app to fetch the audio programmatically, you would just need to build the URL and fetch the audio however bear in mind that this will only work for a few words and sentences, I suppose that people abused the service with thounsands of requests and now Google puts a limit the quantity on audios you can generate to about 15 calls per user, after that limit is reached you will very likely get an <a class='mintip'>unusual traffic<span><img src='../articles/images/deny-tts-google.png'/></span></a> captcha making the service completely unusable for your app... In order to raise the limit again you would need to solve the captcha.

> "Ohh wait! The project is working just lemme answer this captcha to prove that I’m not a robot!”
> -☉_☉

With this project you will be able to create your own Text to Speech server for your apps using the SVOX engine for Ubuntu. Bear in mind that the SVOX speech synthesis quality is far lower than Google's engine. On the bright side, you can flood your Ubuntu server with thousand calls if needed.


Some project ideas that could use this web interface are:
 * A speaking Arduino that talks when you press some buttons.
 * An accessibility app for the blind. Maybe an Android app that reads Barcodes aloud *(there are some good tutorials about [how to read barcodes](http://code.tutsplus.com/tutorials/android-sdk-create-a-barcode-reader--mobile-17162) and [how to read barcodes and QR codes](http://examples.javacodegeeks.com/android/android-barcode-and-qr-scanner-example/))*
 * A computer clock that reads the time every hour (like on Mac).

Find the project and the installation instructions at the Github repo [https://github.com/adelriosantiago/svox-interface-nodejs](https://github.com/adelriosantiago/svox-interface-nodejs). You will need a Virtual Machine running Ubuntu or a Digital Ocean instance in order to get the SVOX TTS engine running and [Node.js](http://nodejs.org) to create the web request interface.

Here is how the finished project looks like:

<a href='http://tts.adelriosantiago.com'>![](articles/images/tts-final.png)</a>

Simply select the language, the text to convert and click on the URL to get the audio. Feel free to play with the finished project generating some phrases at the address [tts.adelriosantiago.com](http://tts.adelriosantiago.com).


