# split-images-shadow

> This is one fork and upgrade from "split-images",  and I upgrade the dependency jimp from 0.6 to 0.16, which have different result when the image has rotation infomation.

## What is it

split-images is a simple package that allows you to split an image to chunks
the chunks are returned as an Array`<Buffer>` (Array of buffers) of the image type provided.

### Supported Images

Image paths, urls and buffers can be used, supported image types are jpeg, png, bmp, tiff and gif.

### npm

`npm i split-images-shadow --save`

### Node versions

Node >= 7.10

## Methods

**`imageToChunks(image,chunkSize)`**

Splits the image horizontaly depending of the chunkSize

> * **`image`** can be a path, a url or a buffer
> * **`chunkSize`** the height in pixels each chunk will be

> returns `Array<Buffer>`

## Examples

**Read from a local file**

```
const fs = require('fs');
const { imageToChunks } = require('split-images-shadow');

(async()=> {
try {
  const chunckSize = 1000;
  const chuncks = await imageToChunks('imgs/test.png',chunckSize);
  console.log('Number of chunks', chuncks.length);

  let i = 0;
  chuncks.forEach(c => {
    i++;
    fs.writeFileSync(`slice_${i}.png`,c);
  });
} catch (e) {
  console.log(e);
}

})();
```

**Read from a url**

```
const fs = require('fs');
const { imageToChunks } = require('split-images-shadow');

(async()=> {
try {
  const chunckSize = 1000;
  const chuncks = await imageToChunks('http://example.com/images/test.png',chunckSize);
  console.log('Number of chunks', chuncks.length);

  let i = 0;
  chuncks.forEach(c => {
    i++;
    fs.writeFileSync(`slice_${i}.png`,c);
  });
} catch (e) {
  console.log(e);
}

})();
```
