# spider-ximage
> www.ximage.pro站点的爬虫,编写目的在于学习promise,以及并发，使用成熟的Pormise库的使用

### About
- 爬图片
- 下载图片
- 存错图片地址以及详情
- 存储图片Referer

### How to start?
```bash
curl -o- https://raw.githubusercontent.com/owen-carter/spider-ximage/master/start.sh | bash
```

### About promise
```ecmascript 6
    async bootstrap() {
        for (let url of this.urlList()) {
            let jsonRes = await Spider.curl(url);
            logger.info(`get a json ${url}`);
            let imageList = this.parseImage(jsonRes);

            Promise.map(imageList, (image) => {
                return this.downImage(image)
            }, this.concurrency).then(() => {
                logger.info(`download ${imageList.length} images`);
            });

        }
    }
```

### Changelog
+ v1.0
    - 可下载整站图片

+ v1.1
    - 引入bluebird
    - 使用Promise.map,并发下载，提高速度
                                     
+ v1.2                           
    - 存储图片Referer                 
    - 存错图片地址以及详情   