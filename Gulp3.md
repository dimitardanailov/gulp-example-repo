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

Minify PNG, JPEG, GIF and SVG images with [imagemin](https://github.com/imagemin/imagemin)

Repository: [https://github.com/sindresorhus/gulp-imagemin](https://github.com/sindresorhus/gulp-imagemin)

##### Installation

npm:
```bash
npm install --save-dev imagemin-pngquant # imagemin pngquant
npm install --save-dev gulp-imagemin # gulp imagemin
```

yarn
```bash
yarn add imagemin-pngquant --dev
yarn add gulp-imagemin --dev
```

##### Usage

```javascript
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

### Gulp Concat

Concatenates files

Repository: [https://github.com/gulp-community/gulp-concat](https://github.com/gulp-community/gulp-concat)


##### Installation

npm:
```bash
npm install --save-dev gulp-concat
```

yarn
```bash
yarn add gulp-concat --dev
```

##### Usage

```javascript
import gulp from 'gulp';
import concat from 'gulp-concat';

gulp.task('scripts', function () {
  return gulp.src('./lib/*.js')
    .pipe(concat('all.js'))
    .pipe(gulp.dest('./dist/'));
});
```

### Gulp order

The gulp plugin gulp-order allows you to reorder a stream of files using the same syntax as of `gulp.src`.

Repository: [https://github.com/sirlantis/gulp-order](https://github.com/sirlantis/gulp-order)

##### Installation

npm:
```bash
npm install --save-dev gulp-order
```

yarn
```bash
yarn add gulp-order --dev
```

##### Usage

```javascript
import gulp from 'gulp';
import order from 'gulp-order';
import coffee from 'gulp-coffee';
import concat from 'gulp-concat';

gulp.task('scripts', function () {
  return gulp.src("**/*.coffee")
    .pipe(coffee())
    .pipe(gulp.src("**/*.js")) // gulp.src passes through input
    .pipe(order([
      "vendor/js1.js",
      "vendor/**/*.js",
      "app/coffee1.js",
      "app/**/*.js"
    })
    .pipe(concat("all.js"))
    .pipe(gulp.dest("dist"));
});
```


### Gulp Wrap

A gulp plugin to wrap the stream contents with a lodash template.

Repository: [https://github.com/adamayres/gulp-wrap](https://github.com/adamayres/gulp-wrap)

##### Installation

npm:
```bash
npm install --save-dev gulp-wrap
```

yarn
```bash
yarn add gulp-wrap --dev
```

##### Usage

```javascript
import gulp from 'gulp';
import wrap from 'gulp-wrap';


gulp.task('scripts', function () {
  return gulp.src("./src/*.json")
    .pipe(wrap('Hello, <%= contents.title %>, have a <%=
    contents.adjective %> day.'))
    .pipe(gulp.dest("./dist"));
});
```

### StreamQueue

StreamQueue pipe the queued streams one by one in order to preserve their content order.

Repository: [https://github.com/nfroidure/StreamQueue](https://github.com/nfroidure/StreamQueue)

##### Installation

npm:
```bash
npm install --save-dev streamqueue
```

yarn
```bash
yarn add streamqueue --dev
```

##### Usage

```javascript
import streamqueue from 'streamqueue';

let queue = new streamqueue();
queue.queue(
  Fs.createReadStream('input.txt'),
  Fs.createReadStream('input2.txt'),
  Fs.createReadStream('input3.txt')
);
queue.done();

queue.pipe(process.stdout);
```
