--
layout: post
title: Fix Angular-fullstack in production mode
--


<p>Given that you are using the <code>Gruntfile.js</code> provided by <strong>angular fullstack</strong> we will edit it and fix the bug I discovered. Change to your project root and type:</p>

<pre><code>$ sudo emacs Gruntfile.js
</code></pre>

<h2 id="fixfontawesomebug">Fix Font-Awesome Bug</h2>

<p>Insert these lines in order to fix <a href="https://github.com/DaftMonk/generator-angular-fullstack/issues/421">Font Awesome</a> and the <a href="https://github.com/DaftMonk/generator-angular-fullstack/issues/792">app.css</a> bug:</p>

<script src="https://gist.github.com/nottinhill/212ea263cc419016016d.js"></script>

<p>In addition to above changes, go into your <code>app.css</code> and change all lines like this; instead of the bower_components directory:</p>

<pre><code>src: url('../assets/fonts/fontawesome-webfont.eot?v=4.1.0');
</code></pre>

<h2 id="figgooglewebfontbug">Fig Google Webfont Bug</h2>

<p>The Build ignores Google font paths. THus go to the top of your bootstrap file, and look for any google web font imports, e.g. at the top of the file:</p>

<p><strong>/bootstrap_components/bootswatch-dist/css/bootstrap.css</strong></p>

<p>We see a </p>

<pre><code>@import url("//fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,700,400italic");
</code></pre>

<p>Minify tasks inside of our grunt task runner will effectively destroy this (at least from my troubleshooting findings I would call it that). In order to fix this bug, we have to hard code the font into the index.html. Yes its ugly,but its a quick fix, so stop complaining. Put this in the top of your index.html file, right after the meta tags and outside the yeoman template comments:</p>

<pre><code> ....
&lt;meta name="viewport" content="width=device-width"&gt;
&lt;link href='http://fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,700,400italic' rel='stylesheet' type='text/css'&gt;
</code></pre>

<h2 id="fiximageminbug">Fix imagemin Bug</h2>

<p>Now you might hit another bug, especially when using a Mac and grunt to build the project:</p>

<p><code>Warning: Running "imagemin:dist" (imagemin) task</code></p>

<p>In order to workaround this bug you usually would:</p>

<pre><code>$ brew install libpng
</code></pre>

<p>then rebuild the imagemin grunt plugin with </p>

<p><code>$ npm install grunt-contrib-imagemin</code></p>

<p>Now, when building with <code>grunt build:dist</code> you are still getting the error about imagemin, try getting the latest MacOSX binary from the git repo with:</p>

<pre><code>git clone https://github.com/imagemin/pngquant-bin.git
sudo cp pngquant-bin/vendor/osx/pngquant /usr/local/bin/
sudo chmod +x /usr/local/bin/pngquant
</code></pre>

<p>Now rebuild imagemin with npm and the error message should be gone. Further troubleshooting can be found here: <a href="https://github.com/gruntjs/grunt-contrib-imagemin/issues/254">https://github.com/gruntjs/grunt-contrib-imagemin/issues/254</a></p>
