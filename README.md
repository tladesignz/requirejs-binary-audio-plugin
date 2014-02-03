# Require.js Plugins for requiring binary and Audio (MP3) files

I hacked this together for a short test.

## Usage:

```javascript

    require.config( {
        paths: {
            bin: '/lib/requirejs-binary-audio-plugin/bin',
            mp3: '/lib/requirejs-binary-audio-plugin/mp3',
        }
    } );

    require(
        [
            'bin!foo',
            'mp3!bar'
        ],
        function( foo, bar )
        {
            console.log( foo ); // Binary data in an ArrayBuffer object.

            console.log( bar ); // PCM decoded audio in an AudioBuffer object.

            window.AudioContext = window.AudioContext || window.webkitAudioContext;
            var context = new AudioContext();

            var source = context.createBufferSource();
            source.buffer = bar;
            source.connect( context.destination );
            source.start( 0 );
        }
    );
```

## See

### Explanation of XHR2, ArrayBuffer and binary data loading:

http://www.html5rocks.com/en/tutorials/file/xhr2/

### Explanation of HTML5 Audio API and AudioContext:

http://www.html5rocks.com/en/tutorials/webaudio/intro/

## License

The MIT License (MIT)

Copyright (c) 2014 Benjamin Erhart

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
