---
title: Optimize Hexo with Gulp
author: Jun Hu
toc: true
date: 2019-08-24 09:38:00
tags:
 - Hexo
 - Gulp

---

Gulp is an open-source JavaScript toolkit created by Eric Schoffstall used as a streaming build system in front-end web development. We can use Gulp to compress the hexo static resources so that accessing our website is becoming faster. There are lots to learn about Gulp but to use it here on our Hexo webte is simple.

<!-- more -->

# Install Gulp
```bash
$ npm install gulp -g
```

# Install modules that will be used soon
```bash
$ npm install gulp-htmlclean gulp-htmlmin gulp-clean-css gulp-uglify gulp-imagemin del --save
```

# Create a gulpfile.js file in the Hexo root folder with below scripts
```java
var gulp = require('gulp');
var minifycss = require('gulp-clean-css');
var uglify = require('gulp-uglify');
var htmlmin = require('gulp-htmlmin');
var htmlclean = require('gulp-htmlclean');
var imagemin = require('gulp-imagemin');
var del = require('del');
var Hexo = require('hexo');

gulp.task('clean', function() {
    return del(['public/**/*']);
});

var hexo = new Hexo(process.cwd(), {});
gulp.task('generate', function(cb) {
    hexo.init().then(function() {
        return hexo.call('generate', {
            watch: false
        });
    }).then(function() {
        return hexo.exit();
    }).then(function() {
        return cb()
    }).catch(function(err) {
        console.log(err);
        hexo.exit(err);
        return cb(err);
    })
});

gulp.task('deploy', function() {
    return hexo.init().then(function() {
        return hexo.call('deploy', {
            watch: false
        }).then(function() {
            return hexo.exit();
        }).catch(function(err) {
            return hexo.exit(err);
        });
    });
});

gulp.task('minify-css', function() {
    return gulp.src('./public/**/*.css')
        .pipe(minifycss({
            compatibility: 'ie8'
        }))
        .pipe(gulp.dest('./public'));
});

gulp.task('minify-html', function() {
    return gulp.src('./public/**/*.html')
        .pipe(htmlclean())
        .pipe(htmlmin({
            removeComments: true,
            minifyJS: true,
            minifyCSS: true,
            minifyURLs: true,
        }))
        .pipe(gulp.dest('./public'))
});

gulp.task('minify-img', function() {
    return gulp.src('./public/images/**/*')
        .pipe(imagemin([
					imagemin.gifsicle({interlaced: true}),
					imagemin.jpegtran({progressive: true}),
					imagemin.optipng({optimizationLevel: 5}),
					imagemin.svgo({
						plugins: [
							{removeViewBox: true},
							{cleanupIDs: false}
								]
							})
						]))
        .pipe(gulp.dest('./public/images'))
});

gulp.task('compress', gulp.series('minify-html', 'minify-css', 'minify-img'));

gulp.task('default', gulp.series('clean', 'generate', 'compress', 'deploy'));
```
Notes:
* Gulp throws an error, as `gulp-uglify` does not support es6 syntax. So I have remoeved it from the above script. But I heard that `gulp-uglify-es` may resolve this and will give it a try later. For now it will compress your css, html and image files only.

* Gulp v4 has introduced some breaking changes and that creates  problems with run-sequence package. Thus I used `gulp.series` instead of `runSequence` otherwise Gulp throws an error like "gulp.hasTask is not a function".

* Hexo clean, depoly and generate have also been added into the above js file, so next time when you wish to depoly your site instead of `hexo clean && hexo g && hexo d && gulp` simply use `gulp`!
```bash
$ gulp
```

---

# **Update_24Aug2019** 

[`gulp-uglify-es`](https://www.npmjs.com/package/gulp-uglify-es) is working!

- Install the plugin 

  ```bash
  $ npm install --save-dev gulp-uglify-es
  ```

- Insert below to `gulpfile.js`

  ```js
  gulp.task('minify-js', function() {
      return gulp.src('./public/**/*.js')
          .pipe(uglify())
          .pipe(gulp.dest('./public'));
  });
  ```
And then you are good to go! `gulp`
  

---


Reference:

*- [Official Website](https://gulpjs.com/)*
*- [Sample of gulpfile.js for hexo generate blog, compress public files](https://gist.githubusercontent.com/zhoujiealex/4d926889b02b85d4d8d73f036ef728eb/raw/649fe189805bd0adc784d33615d6792ba583073c/gulpfile.js)*
*- [An Introduction to JavaScript Automation with Gulp](https://www.toptal.com/nodejs/an-introduction-to-automation-with-gulp)*
*- [gulp-uglify-es](https://www.npmjs.com/package/gulp-uglify-es)*


