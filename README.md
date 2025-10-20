checkimage
---------------

    提示：由于该接口用的人不多，又消耗服务器资源，从2021.12.16开始关闭该接口，且代码已开源，有需求自己搭建。


本项目是一个图片鉴黄`api`接口，支持`jpg`、`png`、`jpeg`格式文件，参考[nsfwjs][1]。

在线项目：https://elysiatools.com/en/tools/nsfw-image-detector

安装步骤
---------------

自行搭建好`ndoejs`环境，使用命令：

    git clone https://github.com/iiiiiii1/checkimage
    cd checkimage
    npm i
    npm i -g pm2
    pm2 start index.js --name checkimage

访问地址：ip:3027，使用看下方演示。

接口地址
---------------

    https://checkimage.querydata.org/api

使用示例
---------------
    
    #/root/xx.png为图片路径
    curl https://checkimage.querydata.org/api -F "image=@/root/xx.png;type=image/jpeg" 

返回信息：

    [
        {
            "className": "Neutral",
            "probability": 0.9277840852737427
        },
        {
            "className": "Drawing",
            "probability": 0.07143104821443558
        },
        {
            "className": "Hentai",
            "probability": 0.0007780276937410235
        },
        {
            "className": "Porn",
            "probability": 0.000005075656645203708
        },
        {
            "className": "Sexy",
            "probability": 0.0000018030658566203783
        }
    ]
类型参考：

    Drawing和Neutral：均为正常图片
    hentai：二次元类型的暴露图片指数
    sexy：露点图片的指数
    porn：就是色情图片的指数
图片指数越高，越接近该类型，最高的基本可以判定为该类型。

  [1]: https://github.com/infinitered/nsfwjs
