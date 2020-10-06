# ugs-nativescript-files-progress ![apple](https://cdn3.iconfinder.com/data/icons/picons-social/57/16-apple-32.png) ![android](https://cdn4.iconfinder.com/data/icons/logos-3/228/android-32.png)

[![npm version](https://badge.fury.io/js/ugs-nativescript-files-progress.svg)](http://badge.fury.io/js/ugs-nativescript-files-progress)

## Introduction

This plugin is a fork from https://github.com/tobydeh/nativescript-download-progress

This plugin allows you to download large files and provides progress updates.

Nativescripts http.getFile method stores the data in memory which can cause out of memory exceptions and doesn't provide progress updates.

## Installation

```javascript
tns plugin add ugs-nativescript-files-progress
```

## Example

```typescript
import { DownloadProgress } from 'ugs-nativescript-files-progress'

const download = new DownloadProgress()
download.addProgressCallback((progress) => {
  console.log('Progress:', progress)
})
download
  .downloadFile('http://ipv4.download.thinkbroadband.com/20MB.zip')
  .then((file) => {
    console.log('Success', file)
  })
  .catch((error) => {
    console.log('Error', error)
  })
```

## Passing request headers

```typescript
import { DownloadProgress } from 'ugs-nativescript-files-progress'

const download = new DownloadProgress()
download.addProgressCallback((progress) => {
  console.log('Progress:', progress)
})
const url = 'http://ipv4.download.thinkbroadband.com/20MB.zip'
const destinationPath = 'some/path/to/file.zip'
const requestOptions: RequestOptions = {
  method: 'GET',
  headers: {
    Authorization: 'Bearer token',
  },
}
download
  .downloadFile(url, requestOptions, destinationPath)
  .then((file) => {
    console.log('Success', file)
  })
  .catch((error) => {
    console.log('Error', error)
  })
```

## License

Apache License Version 2.0, January 2004
