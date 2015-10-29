---
layout: post
title: Fix Grunt file angular-fullstack in production mode
---

Given that you are using the `Gruntfile.js` provided by **angular fullstack** we will edit it and fix the bug I discovered. Change to your project root and type:

    $ sudo emacs Gruntfile.js

## Fix Font-Awesome Bug

Insert these lines in order to fix [Font Awesome](https://github.com/DaftMonk/generator-angular-fullstack/issues/421) and the [app.css](https://github.com/DaftMonk/generator-angular-fullstack/issues/792) bug:

```js
//copy.dist.files
//
{
    // include font-awesome webfonts
    //
    expand: true,
    dot: true,
    cwd: '<%= yeoman.client %>/bower_components/font-awesome',
    src: ['fonts/*.*'],
    dest: '<%= yeoman.dist %>/public/assets'
},{
    // include bootstrap webfonts
    //
    expand: true,
    dot: true,
    cwd: '<%= yeoman.client %>/bower_components/bootstrap/dist',
    src: ['fonts/*.*'],
    dest: '<%= yeoman.dist %>/public/assets'
}

//copy.serve.files (add this target)
    copy: {
      serve: {
        files: [{
          // include font-awesome webfonts
          expand: true,
          dot: true,
          cwd: '<%= yeoman.client %>/bower_components/font-awesome',
          src: ['fonts/*.*'],
          dest: '<%= yeoman.client %>/assets'
        }]
      }

// rev.dist.file.source
//
'<%= yeoman.dist %>/public/assets/fonts/*'

// usemin.options.patterns:
//
css: [
   [/(..\/fonts\/)/g, 'Fix webfonts path', function(match) {
      return match.replace('../fonts/', '../assets/fonts/');
    }]
]
    
// Prevent app.css index.html injection
  css: {
    options: {
      transform: function(filePath) {
        filePath = filePath.replace('/client/', '');
        filePath = filePath.replace('/.tmp/', '');
        return '<link rel="stylesheet" href="' + filePath + '">';
      },
      starttag: '<!-- injector:css -->',
      endtag: '<!-- endinjector -->'
    },
    files: {
      '<%= yeoman.client %>/index.html': [
        '<%= yeoman.client %>/{app,components}/**/*.css',
        '!<%= yeoman.client %>/app/app.css'  //this is the line to be added to prevent app.css from being loaded twice  --
      ]
    }
}
```

In addition to above changes, go into your `app.css` and change all lines like this; instead of the bower_components directory:

```
src: url('../assets/fonts/fontawesome-webfont.eot?v=4.1.0');
```

## Fix Google Webfont Bug

The Build ignores Google font paths. Thus go to the top of your bootstrap file, and look for any google web font imports, e.g. at the top of the file:

```
/bootstrap_components/bootswatch-dist/css/bootstrap.css
```

We see a

```
@import url("//fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,700,400italic");
```

Minify tasks inside of our grunt task runner will effectively destroy this (at least from my troubleshooting findings I would call it that). In order to fix this bug, we have to hard code the font into the index.html. Yes its ugly,but its a quick fix, so stop complaining. Put this in the top of your index.html file, right after the meta tags and outside the yeoman template comments:
```html
....
<meta name="viewport" content="width=device-width">
<link href='http://fonts.googleapis.com/css?family=Source+Sans+Pro:300,400,700,400italic' rel='stylesheet' type='text/css'>
```

## Fix imagemin Bug

Now you might hit another bug, especially when using a Mac and grunt to build the project:

```
Warning: Running "imagemin:dist" (imagemin) task`
```

In order to workaround this bug you usually would:

    $ brew install libpng

then rebuild the imagemin grunt plugin with

```
$ npm install grunt-contrib-imagemin
```

Now, when building with `grunt build:dist` you are still getting the error about imagemin, try getting the latest MacOSX binary from the git repo with:

    git clone https://github.com/imagemin/pngquant-bin.git
    sudo cp pngquant-bin/vendor/osx/pngquant /usr/local/bin/
    sudo chmod +x /usr/local/bin/pngquant

Now rebuild imagemin with npm and the error message should be gone. Further troubleshooting can be found here: [https://github.com/gruntjs/grunt-contrib-imagemin/issues/254](https://github.com/gruntjs/grunt-contrib-imagemin/issues/254)
