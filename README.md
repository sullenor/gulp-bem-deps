# gulp-bem-deps
Ideas about implementing "deps" technology as a gulp-plugin similar to "enb/tech/deps".

## Possible usage

```javascript
var concat = require('gulp-concat');
var deps = require('gulp-bem-deps');

gulp.task('js', function () { // could be any other tech
  var dirsContainingBlocks = ['app/desktop'];
  var options = ['b-*']; // bemjson or may be predefined list of blocks via globing syntax
  
  deps(dirsContainingBlocks, options) // stream, which returns data similar to deps.js (or may be not :))
    .pipe(deps.tech('js')) // additional transform stream, which returns list of '*.js' files
    .pipe(concat('index.js')
    .pipe(gulp.dest('static'));
});
```

## Benefits

- Easy to split stream to multiple technologies: js, css and etc.
- Easier to automate making documentation about the project (list of blocks, their mods and etc).
