# bluebird-yield [![npmjs.com][npmjs-img]][npmjs-url] [![The MIT License][license-img]][license-url]

> Simple function to add support for yielding ES6 generators, iterators, arrays and objects from Bluebird.coroutine()

## Install
```
npm install bluebird-yield
```


## Usage

```js
// At the begging of you project add a yield handler
const Bluebird = require('bluebird');
Bluebird.coroutine.addYieldHandler( require('bluebird-yield') );

// You can now start yielding generators, iterators,
// thunks, arrays and objects


// In some other file...
const Bluebird = require('bluebird');

const rateMovies = Bluebird.coroutine(function * () {
   const data = yield {
     movies: fromPromise('movies'),
     reviewers: fromPromise('reviewers')
   };

   const ratings = {};

   for (let movie of data.movies) {
      let totalRating = 0;
      for (let author of data.authors) {
         yield* rateMove(author, movie);
      }

      ratings[movie.title] = totalRating / data.authors.length;
   }

   return ratings;
});
```

[npmjs-url]: https://www.npmjs.com/package/bluebird-yield
[npmjs-img]: https://img.shields.io/npm/v/bluebird-yield.svg?label=bluebird-yield

[license-url]: https://github.com/a-s-o/bluebird-yield/blob/master/LICENSE
[license-img]: https://img.shields.io/badge/license-MIT-blue.svg
