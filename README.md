CallJs for ES7 async and await
==============================

This is the wrapper around node js http module, and the call function returns a promise object.

__**Installation:**__

```javascript
  git clone https://github.com/iDhruv22/call.git
  cd call
  npm install
  npm start
```

__**Example:**__

__Single request:__

```javascript

  var call = require('./index');

  async function makecall() {

    // Same options those are being use in NodeJS http module -
    // Refer - http://nodejs.org/api/http.html#http_http_request_options_callback
    var options = {
      host: 'jsonplaceholder.typicode.com',
      path: "/posts/1"
    };

    var data = await call.request(options);  // wait will request completes

    console.log(data);  // result
  }
  makecall();

```
__Parallel request:__

```javascript

  var call = require('./index');

  async function makeParallelCalls() {
    var requests = [
      call.request({
        host: 'jsonplaceholder.typicode.com',
        path: "/posts/1"
      }),
      call.request({
        host: 'jsonplaceholder.typicode.com',
        path: "/posts/2"
      }),
      call.request({
        host: 'jsonplaceholder.typicode.com',
        path: "/posts/3"
      })
    ];

    var data = await call.parallel(requests);  // wait till all requests completes 
    console.log(data[0]);  // result of 1st request
    console.log(data[1]);  // result of 2nd request
    console.log(data[2]);  // result of 3nd request
  }

  makeParallelCalls();

```


__**MIT License**__

Copyright (c) 2017 iDhruv22

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
