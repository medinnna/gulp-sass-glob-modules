gulp-sass-glob-modules
=====================

Gulp task to allow importing directories in your SASS/SCSS using `@use` and `@forward`.

## Installation

```
npm install gulp-sass-glob-modules -D
```

## Usage

#### In your sass/scss file:

```scss
@forward "some/path/*";

// becomes
// @forward "some/path/file1.scss";
// @forward "some/path/file2.scss";
// ...

@use "some/path/*";

// becomes
// @use "some/path/file1.scss";
// @use "some/path/file2.scss";
// ...

@use "some/path/*" as *;

// becomes
// @use "some/path/file1.scss" as *;
// @use "some/path/file2.scss" as *;
// ...

```

#### In your gulpfile:

```js
import batchSass from 'gulp-sass-glob-modules';

gulp.task('css', function() {
  return gulp
    .src(srcDir + 'stylesheets/app.scss')
    .pipe(batchSass())
    .pipe(
      sass({
        includePaths: ['src/stylesheets']
      }))
    .pipe(gulp.dest('./public/css/'));
});
```

