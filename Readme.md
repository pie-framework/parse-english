# parse-english [![Build Status](https://img.shields.io/travis/wooorm/parse-english.svg)](https://travis-ci.org/wooorm/parse-english) [![Coverage Status](https://img.shields.io/coveralls/wooorm/parse-english.svg)](https://coveralls.io/r/wooorm/parse-english?branch=master) [![Code Climate](http://img.shields.io/codeclimate/github/wooorm/parse-english.svg)](https://codeclimate.com/github/wooorm/parse-english)

**parse-english** is an English language parser in JavaScript. NodeJS, and the browser. Based on [parse-latin](https://github.com/wooorm/parse-latin "ParseLatin").

## Installation

npm:
```sh
$ npm install parse-english
```

Component:
```sh
$ component install wooorm/parse-english
```

Bower:
```sh
$ bower install parse-english
```

## Usage

````js
var Parser = require('parse-english'),
    parser = new Parser();

/* parse-latin would fail helplessly at the full-stop preceding the
 * capital `H`, and would erroneously parse the following as two
 * sentences. */
parser.tokenizeRoot('Mr. Henry Brown: A hapless but friendly City of London worker.');
/*
 * ˅ Object
 *      type: "RootNode"
 *    ˅ children: Array[1]
 *       ˅ 0: Object
 *            type: "ParagraphNode"
 *          ˅ children: Array[1]
 *             ˅ 0: Object
 *                  type: "SentenceNode"
 *                ˃ children: Array[24]
 *             ˃ __proto__: Array
 *          ˃ __proto__: Object
 *       ˃ __proto__: Array
 *    ˃ __proto__: Object
 */
````

## API

parse-english has the same [API as parse-latin](https://github.com/wooorm/parse-latin#api "ParseLatin API"), but returns results better suited for English natural language.

Support includes:

* Unit abbreviations (tsp., tbsp., oz., ft., &c.);
* Time references (sec., min., tues., thu., feb., &c.);
* Business Abbreviations (Inc. and Ltd);
* Social titles (Mr., Mmes., Sr., &c.);
* Rank and academic titles (Dr., Rep., Gen., Prof., Pres., &c.);
* Geographical abbreviations (Ave., Blvd., Ft., Hwy., &c.);
* American state abbreviations (Ala., Minn., La., Tex., &c.);
* Canadian province abbreviations (Alta., Qué., Yuk., &c.);
* English county abbreviations (Beds., Leics., Shrops., &c.);
* Common elision (omission of letters) ('n', 'o, 'em, 'twas, '80s, &c.).

## Benchmark

Run the benchmark yourself:

```sh
$ npm run benchmark
```

On a MacBook Air, it parser about 3 large books, 60 big articles, or 6,146 paragraphs per second.

```
              parser.parse(source);
   6,146 op/s » A paragraph (5 sentences, 100 words)
     659 op/s » A section (10 paragraphs, 50 sentences, 1,000 words)
      59 op/s » An article (100 paragraphs, 500 sentences, 10,000 words)
       3 op/s » A (large) book (1,000 paragraphs, 5,000 sentences, 100,000 words)
```

## Related

  * [parse-latin](https://github.com/wooorm/parse-latin "ParseLatin")
  * [parse-dutch](https://github.com/wooorm/parse-dutch "ParseDutch")
  * [retext](https://github.com/wooorm/retext "Retext")
  * [textom](https://github.com/wooorm/textom "TextOM")

## License

MIT © Titus Wormer
