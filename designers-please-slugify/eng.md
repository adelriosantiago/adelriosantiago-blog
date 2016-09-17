<permalink>eng</permalink>
<month>3</month>
<year>2014</year>

# Designers: Please slugify your files!

It is very common for designers to name their files with spaces and special characters like "Left Arrow (6)" or "Background & Color Palette for XYZ!". These names are OK if you are only planning to share these files within the design department. However, most of the times, these assets are required by de software & mobile department, who will then build a website or mobile app. 

There are several reasons why naming your images with special characters and spaces is a bad idea, especially for mobile projects. Image resources with special characters create ugly-looking web requests and for mobile development -especially Android- file names are restricted to only alphanumerics (a-z, 0-9 and _).

<hidden>add the reasons why it is a bad idea here</hidden>
<hidden>todo: implement http://foundation.zurb.com/sites/docs/v/5.5.3/components/forms.html input label with .com </hidden>

Here is a small tool you can use to slugify your file and folder names. Use it to save some time to your software development team. It will also help you having a *cleaner and better organized computer desk*.
 
<form>
	<div class="row">
		<div class="large-12 columns">
			<label>String to slugify
				<input class="in" type="text" placeholder="large-12.columns" />
			</label>
		</div>
	</div>
	<div class="row">
		<div class="large-12 columns">
			<label>Pretty slug (good for website assets in general)
				<input class="pretty-slug" type="text" readonly="readonly" />
			</label>
		</div>
		<div class="large-12 columns">
			<label>RFC3986 slug (same as above, accepts dots)
				<input class="rfc3986-slug" type="text" readonly="readonly" />
			</label>
		</div>
		<div class="large-12 columns">
			<label>Android images (a restrictive pattern for Android mobile app resources)
				<input class="android-slug" type="text" readonly="readonly" />
			</label>
		</div>
	</div>
</form>

<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.15.0/lodash.min.js"></script>
<script src="/articles/designers-please-slugify/js/slug.js"></script>
<script>
	$(function () {
		$('input.in:visible').on('keyup', function (el) {
			console.log($(this).val());
			$('input.pretty-slug').val(slug($(this).val()));
			$('input.rfc3986-slug').val(slug($(this).val(), { mode: "rfc3986" }));
			$('input.android-slug').val(_.lowerCase(slug($(this).val(), { mode: "pretty" })));
		});
	});
</script>

<br/>

<hidden>

Es muy común encontrar diseñadores que nombran las imagenes con textos como "Flecha arriba.png" o "Flecha abajo.jpg", lo cual genera trabajo extra para los programadores que tienen que "slug-ificar" los nombres para que puedan ser usados en el proyecto web o movil.

TLDR: if you don't want to read the reasons why naming images like this is a bad idea then just type the name of the image you are about to send your programmer and rename it with the output, use the app shown below
this pretends to be a small piece of advice to designers: please slugify your image names!
slugify or to slug means to make the name programmer friendly, usually designers tend to name their images with names like "Left Arrow (6)" or "Background & Color Palette for XYZ", there are many reasons why these names are not good names, these are:
-spaces are not program friendly: yes, computer programs and this mistyrious blank space " " are not friends, in fact computers actually have no trouble with this space, afterall everything is a number for the computer, however not allowing spaces on filenames is wise, otherwise you could create two images, one called " " and the other one called "  ". It is normally safe to replace all spaces with the character "-".
-names must be in lowercase: the image "ICON.png" and "icon.png" are two different images for most of the operating systems out there, to prevent that many coding conventions requiere that your images must be in lowercase
-special characters may cause issues: it is a bad idea to name images with special characters like ª!"·$%&/()=?¿ if you do so you can break a working program, these caracters are sometimes used as an indication to perform other actions, for example the character & and ? is used in WWW to send parameters to the server (i.e. www.example.com/?where=here&date=today)
also, as a last but not least, bear in mind that names should be descriptive, instead of naming a set of images like "UP Arrow.png", "DOWN Arrow.png" name them "arrow-up.png" and "arrow-down.png", this way all arrows will be next to each other when browsing the assets folder.

designers: here is a small app that helps you naming images, just type the name of your image you want to convert and it will be slugified.

mayn times I have seen that designers tend to use names that don't

</hidden>