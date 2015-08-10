<permalink>Text-to-speech-Nodejs</permalink>
<month>8</month>
<year>2015</year>

# Setting up your own Text To Speech server on the web with Node.js and Ubuntu

You probably already know that Google has a service to convert text to audio via the Google Translate engine. You can easily test it by clicking on the [megaphone icon] to read the text aloud. [Inspecting the button with the browser toolbar] we find that what is actually going on behind the scenes is a call to an address with the text we want to read aloud, so that when you click on the megaphone you are actually performing a request like these

 * [] To read “hello world” in english,
 * [] To read aloud “buon giorno” in italian,

and so on with other languages.

You can now imagine yourself creating and Android or Arduino app to fetch the audio programmatically, however bear in mind that this will only work for a few words and sentences, Google now limits the quantity on requests you can perform to about 15 per user, after that limit is reached you will very likely get an [unusual traffic] captcha inquiry making the service completely unusable from a programatical point of view... 

> "Ohh wait! The project is working just lemme answer this captcha to prove I’m a human!”
> -☉_☉

You can find the project and the installation instructions at the Github repo []. You will need a Virtual Machine running Ubuntu (or a Digital Ocean instance) in order to get the SVOX TTS engine running and Node.js to create the web request interface.

Feel free to play with the finished project [here] generating some words and sentences to audio.

Some project ideas that could use this engine are:
 * A speaking Arduino that talks when you press some buttons.
 * An accessibility app for the blind. Maybe an Android app that reads Barcodes aloud *(there are some good tutorials about how to read barcodes like [this] and [this])*
 * A computer clock that reads the time every hour (like on Mac).

Having said that I have to mention that 

> EDIT: I recently had to put a limit on the request per users, which suddenly increased to several thousand of words being created... I’m not sure if it was an attempt to drop the server or just someone hungry for audios. Remember that running the project on your local computer is considerably faster than doing a call to the web. From now on after generating several audios you should see a Google NoCaptcha! By the way, just for the record, the new NoCaptcha from Google is just awesome! It only shows [small checkbox that says “I’m not a robot”] and when you check it, it correctly determines (most of the times) if you are a real person or not! I just ask myself: How come do they do that!? What kind of black magic is that!? I’m really curious to know how it works...




---
---
---






## Getting Started

The bare minimum for using highlight.js on a web page is linking to the library
along with one of the styles and calling [`initHighlightingOnLoad`][1]:

```html
<link rel="stylesheet" href="/path/to/styles/default.css">
<script src="/path/to/highlight.pack.js"></script>
<script>hljs.initHighlightingOnLoad();</script>
```

This will find and highlight code inside of `<pre><code>` tags; it tries to detect
the language automatically. If automatic detection doesn’t work for you, you can
specify the language in the `class` attribute:

```html
<pre><code class="html">...</code></pre>
```

The list of supported language classes is available in the [class reference][8].
Classes can also be prefixed with either `language-` or `lang-`.

To disable highlighting altogether use the `nohighlight` class:

```html
<pre><code class="nohighlight">...</code></pre>
```

## Custom Initialization

When you need a bit more control over the initialization of
highlight.js, you can use the [`highlightBlock`][2] and [`configure`][3]
functions. This allows you to control *what* to highlight and *when*.

Here’s an equivalent way to calling [`initHighlightingOnLoad`][1] using jQuery:

```javascript
$(document).ready(function() {
  $('pre code').each(function(i, block) {
    hljs.highlightBlock(block);
  });
});
```

You can use any tags instead of `<pre><code>` to mark up your code. If you don't
use a container that preserve line breaks you will need to configure
highlight.js to use the `<br>` tag:

```javascript
hljs.configure({useBR: true});

$('div.code').each(function(i, block) {
  hljs.highlightBlock(block);
});
```

For other options refer to the documentation for [`configure`][3].


## Getting the Library

You can get highlight.js as a hosted or custom-build browser script or as a
server module. Head over to the [download page][4] for all the options.

**Note:** the library is not supposed to work straight from the source on
GitHub; it requires building. If none of the pre-packaged options work for you
refer to the [building documentation][5].


## License

Highlight.js is released under the BSD License. See [LICENSE][10] file for
details.


## Links

The official site for the library is at <https://highlightjs.org/>.

Further in-depth documentation for the API and other topics is at
<http://highlightjs.readthedocs.org/>.

Authors and contributors are listed in the [AUTHORS.en.txt][9] file.

[1]: http://highlightjs.readthedocs.org/en/latest/api.html#inithighlightingonload
[2]: http://highlightjs.readthedocs.org/en/latest/api.html#highlightblock-block
[3]: http://highlightjs.readthedocs.org/en/latest/api.html#configure-options
[4]: https://highlightjs.org/download/
[5]: http://highlightjs.readthedocs.org/en/latest/building-testing.html
[8]: http://highlightjs.readthedocs.org/en/latest/css-classes-reference.html
[9]: https://github.com/isagalaev/highlight.js/blob/master/AUTHORS.en.txt
[10]: https://github.com/isagalaev/highlight.js/blob/master/LICENSE