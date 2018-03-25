gulp-bem-bundler-fs
===================

*DEPRECATED repository, moved to mono repository [gulp-bem](https://github.com/bem/gulp-bem/tree/master/packages/gulp-bem-bundler-fs)*

Install
-------

```
$ npm install --save-dev gulp-bem-bundler-fs
```

Usage
-----

```js
const bundler = require('gulp-bem-bundler-fs');
const Builder = require('gulp-bem-bundle-builder');

const concat = require('gulp-concat');
const stylus = require('gulp-stylus');
const postcss = require('gulp-postcss');
const autoprefixer = require('autoprefixer');
const postcssUrl = require('postcss-url');

// Configuring builder
const builder = Builder();

bundler('*.bundles/*')
    .pipe(builder({
        css: bundle => bundle.src('css')
            .pipe(stylus())
            .pipe(postcss([
                autoprefixer({
                    browsers: ['ie >= 10', 'last 2 versions', 'opera 12.1', '> 2%']
                }),
                postcssUrl({ url: 'inline' })
            ]))
            .pipe(csso())
            .pipe(concat(`${bundle.name}.css`))
    }));
```
