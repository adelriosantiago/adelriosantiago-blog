<permalink>Text-to-speech-Nodejs</permalink>
<month>8</month>
<year>2015</year>

# Create your own Text to Speech API service in Node.js & Ubuntu

In this tutorial I quickly explain how to create your own TTS API online service that you can use for your personal projects that requiere converting text to audio.

In case you don't know Google Translate already has this service  for example you can convert the text "Hi, I'm John Doe" with the link http://translate.google.com/translate_tts?tl=en&q="Hi, I'm John Doe"

For example to conver "Hello world" to audio you simply write this query `http://translate.google.com/translate_tts?tl=en&q="Hello world"` test this clicking [here](http://translate.google.com/translate_tts?tl=en&q=%22Hello%20world%22)


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