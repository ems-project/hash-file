# hash-file
NPM module that compute a file hash from a JavaScript file handler. It provides also some callback function in order to provide user feedbacks.

## Usage

```javascript

    defaultCallbackFinal = function(hash, duration, fileSize, chunkTotal, chunkReorder) {
        console.log('Computed hash: ' + hash + ' in ' + duration + 'seconds (#chunks: ' + chunkTotal + ', #reorder: ' + chunkReorder + '). File size: ' + HashFile.humanFileSize(fileSize));
    }
    
    defaultCallbackProgress = function(percentage, duration, treatedSize, fileSize, chunkTotal, chunkReorder) {
        console.log('File hash in progress ' + percentage + '% after ' + duration + ' seconds (' + HashFile.humanFileSize(treatedSize) + '/' + HashFile.humanFileSize(fileSize) + ') (#chunks: ' + chunkTotal + ', #reorder: ' + chunkReorder + ')');
    }

    new HashFile(file, callbackHashFinal, callbackHashProgress, this, 'sha1');
```

Parameters:
 - `file` : [File object](https://www.w3.org/TR/FileAPI/#file-section)
 - `callbackHashFinal` : callback function called when the hash is available
 - `callbackHashProgress` : callback function called when a file's chunk has been treated
 - `this` : callback function's context
 - `'sha1'` : [CryptoJS hash algorithm](https://cryptojs.gitbook.io/docs/#hashing)
   - Available algorithms: md5, sha1, sha256, sha512, sha3, ripemd160


