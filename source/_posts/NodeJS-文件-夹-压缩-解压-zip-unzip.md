---
title: NodeJS 文件(夹)压缩/解压(zip/unzip)
date: 2017-03-23 17:56:48
tags: nodeJs/zip/unzip
categories: nodeJs
---
我使用的比较靠谱的,也比较简单.其中archiver很强大支持zip格式tar格式,只需要提供路径就可以压缩已存在的文件夹.

压缩：
```javascript
   var fs = require('fs');
   var archiver = require('archiver');

   var output = fs.createWriteStream('archiver-unzip.zip');
   var archive = archiver('zip');

   archive.on('error', function(err){
        throw err;
    });

   archive.pipe(output);
   archive.bulk([
       { src: ['archiver/**']}
   ]);
   archive.finalize();
```
解压:
```javascript
    var fs = require("fs");
    var unzip = require("unzip");

    fs.createReadStream('archiver-unzip.zip').pipe(unzip.Extract({ path: 'unarchive' }));
```