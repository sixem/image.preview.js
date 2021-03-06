# hover-preview-js
<img alt="npm" src="https://img.shields.io/npm/v/hover-preview-js?style=flat-square"> <img alt="Travis (.com)" src="https://img.shields.io/travis/com/sixem/hover-preview-js?style=flat-square">

A simple plugin that adds hoverable image and video previews to any element.

* No dependencies.
* Browser, ES6 and CommonJS support.

A demo of the script can be found [here](https://five.sh/demo/hover-preview/).

## Usage

### Install via npm
`npm install hover-preview-js`

or if using it directly in the browser:

```html
<script type="text/javascript" src="./dist/hover-preview.min.js"></script>
```
### Include the script
```javascript
// CommonJS
const hoverPreview = require('hover-preview-js');

// ES6
import hoverPreview from 'hover-preview-js';

// if importing it as a <script> in the browser
const hoverPreview = window.hoverPreview;
```
### Example Usage
An example element. The script will look for the preview URL in `data-src`, `src` and `href` in that order, or if a `source` option is passed, then that will take priority over everything else.
```html
<div class="preview" data-src="./DSCF3570sss_1.jpg">DSCF3570sss_1.jpg (2,167 kB)</div>
```
Pass elements to the script.
```javascript
// apply it to a single element
var preview = hoverPreview(document.querySelector('div.preview'),
{
	delay : 100, // sets a delay before the preview is shown
	cursor : true // enables a loading cursor while the preview is loading
});

// apply it to multiple elements
var previews = [...document.querySelectorAll('.preview')].map((element, index) =>
{
	return hoverPreview(element, {
		source : `/image_${index}.jpg`
	});
});

// functions
preview.reload(); // reloads the instance
preview.destroy(); // removes all event listeners from the instance
```

## Options

#### `source`
Sets the preview source directly. This will override any `data-src`, `src` and `href` attribute.
##### Default: `null`

#### `delay`
Enables a hover delay (`ms`) before the preview is triggered.
##### Default: `75`

#### `cursor`
Adds a temporary loading cursor while the preview is loading.
##### Default: `true`

#### `encodeAll`
Encodes a few extra characters (`#` and `?`) when processing the URL.
##### Default: `false`

## License

MIT License

Copyright (c) 2020 ему (sixem)

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