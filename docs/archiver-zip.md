##使用Aarchiver 实现工程对build出来的dist目录压缩打包成zip文件

> 先准备一个用压缩打包的zip.js文件
pkg zip.js
```
const fs = require('fs')
const archiver = require('archiver')
const path = require('path')

// 先创建一个dist.zip文件，存放在执行这个文件的当前目录[如果在根据目录通过 node 来执行此文件，文件生成就存放在根目录]
let output = fs.createWriteStream('./dist.zip')
let outputPath = path.normalize(`${__dirname}/../dist.zip`)
// 设置压缩级别
let archvie = archiver('zip', { zlib: { level: 9 } })

output.on('close', function() {
  console.log(outputPath)
  console.log(archive.pointer() + ' total bytes');
  console.log('archiver has been finalized and the output file descriptor has closed.');
})

output.on('end', function() {
  console.log('Data has been drained');
})

archive.on('warning', function(err) {
  if (err.code === 'ENOENT') {
    // log warning
  } else {
    // throw error
    throw err;
  }
})

archive.on('error', function(err) {
  throw err;
})

archive.pipe(output)

archive.directory('dist/', false)

archive.finalize()

```

> 在package.json 的 script 配置 命令执行 此文件。
```
{
  'scripts': {
    pkg: "node zip.js"
  }
}
```
