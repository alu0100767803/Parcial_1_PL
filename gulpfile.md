Complete las partes que faltan del siguiente gulpfile.js en el que se lleva a cabo una tarea para la optimización (uglify/minify) de la aplicación de la práctica de la temperatura:
~~~
/tmp/pl-grado-temperature-converter(karma)]$ cat gulpfile.js


var gulp    = require('gulp'),
gutil   = require('gulp-util'),
uglify  = require('gulp-uglify'),
concat  = require('gulp-concat');
var minifyHTML = require('gulp-minify-html');
var minifyCSS  = require('gulp-minify-css');

gulp.task('minify', function () {
  gulp.src('temperature.js')
  .pipe(uglify())
  .pipe(gulp.dest('minified'));

  gulp.src('./index.html')
  .pipe(minifyHTML())
  .pipe(gulp.dest('./minified/'))

  gulp.src('./*.css')
  .pipe(minifyCSS({keepBreaks:true}))
  .pipe(gulp.dest('./minified/'))
  });
  ~~~
  Explique los pasos para publicar un libro GitBook en GitHub usando gulp
  ~~~
  var gulp = require('gulp');
  var ghPages = require('gulp-gh-pages');

  gulp.task('deploy', function() {
    return gulp.src('./minified/**/*')
    .pipe(ghPages());
    });
    ~~~
  Explique los pasos para actualizar automáticamente los HTML del libro GitBook en su máquina virtual del iaas usando gulp

  var gulp = require('gulp');
  var shell = require ('gulp-shell');

  ¿?¿?¿?¿?¿?¿?
  gulp.task ('actualizar', shell.task(['ssh prolen cp /public' /book/]))
  ¿?¿?¿?¿?¿?¿?
