# Gulp

### Materials
  - Official Documentation
    * Official Website: [http://gulpjs.com/](gulpjs.com)
    * Github Repository: [https://github.com/gulpjs/gulp](https://github.com/gulpjs/gulp)
  - Recipes
    * [https://github.com/gulpjs/gulp/tree/master/docs/recipes](https://github.com/gulpjs/gulp/tree/master/docs/recipes)
  - Courses
    * [Web Tooling & Automation - Gulp, Sass, and BabelJS, Oh My!](https://github.com/gulpjs/gulp/tree/master/docs/recipes)
  - Articles
    * [Grunt vs Gulp - Beyond the Numbers](https://jaysoo.ca/2014/01/27/gruntjs-vs-gulpjs/)
    * [Why I Left Gulp and Grunt for npm Scripts](https://medium.freecodecamp.org/why-i-left-gulp-and-grunt-for-npm-scripts-3d6853dd22b8)

### Gulp Imagemin

Gulp Imagemin Documentation

Minify PNG, JPEG, GIF and SVG images with [imagemin](https://github.com/imagemin/imagemin)

Repository: [https://github.com/sindresorhus/gulp-imagemin](https://github.com/sindresorhus/gulp-imagemin)

##### Installation

npm:
```
npm install --save-dev imagemin-pngquant # imagemin pngquant
npm install --save-dev gulp-imagemin # gulp imagemin
```

yarn
```
yarn add imagemin-pngquant --dev
yarn add gulp-imagemin --dev
```

##### Usage

```
import gulp from 'gulp';
import imagemin from 'gulp-imagemin';
import pngquant from 'imagemin-pngquant';

gulp.task('default', function () {
	return gulp.src('src/images/*')
		.pipe(imagemin({
			progressive: true,
			svgoPlugins: [{removeViewBox: false}],
			use: [pngquant()]
		}))
		.pipe(gulp.dest('dist/images'));
});
```
