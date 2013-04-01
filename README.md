tinysong-coffee
===============

A tiny library for accessing [tinysong.com](http://www.tinysong.com).

An API key is required. You can get one from here: [http://tinysong.com/api](http://tinysong.com/api).

Implements three methods as documented in the official [API documentation](http://tinysong.com/api).

See also: [grooveshark-coffee](https://github.com/raneksi/grooveshark-coffee)

---

### Installation

    npm install tinysong

### Usage

    var tinysong = require('tinysong');

    tinysong.API_KEY = 'your_api_key_here';

    // Get a single result as URL
    tinysong.a('Fall At Your Feet', function(err, res) {
        // res => http://tinysong.com/1bne7
    });

    // Get a single song as an object with metadata
    tinysong.b('Fall At Your Feet', function(err, res) {
        // res => { Url, SongID, SongName, … }
    });

    // Same as `b` but get multiple results, defaults to 5
    tinysong.s('River Flows In You', 10, function(err, res) {
        // res => [ {…}, {…}, … ]
    });

### Note on rate limiting

There's no official documentation on the rate limiting, but it seems to be
something like a few hundred calls per day, after which the requests will
return `rate limit exceeded, please contact us at support@grooveshark.com`.
Therefore Tinysong is not recommended for a huge amount of calls.
