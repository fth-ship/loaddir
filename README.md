loaddir.js
==========

Asset watching, handling, compiling, and insertion into page for node.js

To install run `npm install loaddir`

Some examples
=============

```javascript
// load server side templates into object for use: template.index()
loaddir = require('loaddir');
jade = require('jade');

templates = loaddir({
  as_object: true,
  path: __dirname + '/templates',
  compile: function(){
    jade.compile(this.fileContents);
  }
});

```

in coffeescript:
```coffeescript
loaddir = require 'loaddir'
CoffeeScript = require 'coffee-script'

# compile assets to public for express to serve
loaddir
  path: __dirname + '/frontend/coffeescripts',
  destination: __dirname + '/public/javascripts'
  compile: -> CoffeeScript.compile @fileContents
  to_filename: -> @baseName + '.js'
```

PATCH NOTES
===========
`0.2.12`
Everything got changed to be class based -- use `expose_hooks: true` to get instances of the classes rather than just the outputted results

`0.0.21`
fixed an issue where deleted files were throwing an error to what was watching them
`0.0.20`
removed in issue where files were being watched multiple times if a directory had new files being created or destroyed in it(even swp files were breaking it)

## License

(The MIT License)

Copyright (c) 2009-2012 TJ Holowaychuk &lt;tj@vision-media.ca&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
