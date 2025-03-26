> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [www.cnblogs.com](https://www.cnblogs.com/fuminer/p/17259291.html)

> 一般用于股票等类型网站 http协议 import requests # http协议..... url = "http://43.push2.eastmoney.com/api/qt/stock/trends2/sse?fields1=f1,f2,f3,f4,f5,f6,f7,f8,f9

一般用于股票等类型网站

http 协议
=======

[![](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193907656-300184303.png)](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193907656-300184303.png)

[![](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193909037-332395297.png)](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193909037-332395297.png)

python

```
import requests



# http协议.....

url = "http://43.push2.eastmoney.com/api/qt/stock/trends2/sse?fields1=f1,f2,f3,f4,f5,f6,f7,f8,f9,f10,f11,f12,f13,f17&fields2=f51,f52,f53,f54,f55,f56,f57,f58&mpi=1000&ut=fa5fd1943c7b386f172d6893dbfba10b&secid=1.603896&ndays=1&iscr=0&iscca=0&wbp2u=|0|0|0|web"



headers = {

    "Referer": "http://q![image-20230326193202339](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193909691-38103348.png)uote.eastmoney.com/",

    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/110.0.0.0 Safari/537.36"

}



# 对于服务器返回的是流的时候.可以用stream参数

resp = requests.get(url, headers=headers, stream=True)



data = resp.iter_lines().__next__()

print(data)
```

websocket 协议
============

[![](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193910316-1938261573.png)](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193910316-1938261573.png)

[![](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193910861-2027137586.png)](https://img2023.cnblogs.com/other/2867340/202303/2867340-20230326193910861-2027137586.png)

python

```
# websocket

# 1. ws或wss协议

# 2. 状态码是101





# pip install websockets

# 我们只需要一个可以发送内容以及接受内容的地方

import websockets

import asyncio





async def send(ws):

    await ws.send("")





async def recv(ws):

    await ws.recv()





async def main():

    url = "wss://hq.sinajs.cn/wskt?list=sz399006"

    # url = "wss://hq.sinajs.cn/wskt?list=bj430047,bj430047_i"

    # extra_headers给ws 传递请求头.

    async with websockets.connect(url, extra_headers={

        "Origin": "https://finance.sina.com.cn",

        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/110.0.0.0 Safari/537.36"

    }) as ws:

        # 1. 接一个发一个.  单线程....

        # while 1:

        #     await ws.send("")

        #     ret = await ws.recv()

        #     print(ret)

        # 2. 不定时的发送. 不定时的接收.

        # t1 = asyncio.create_task(send(ws))

        # t2 = asyncio.create_task(recv(ws))

        # await asyncio.wait([t1, t2])



        # 本案例中. 只需要接受一次即可.

        msg = await ws.recv()

        print(msg)

        print(ws)





if __name__ == '__main__':

    asyncio.run(main())
```

*   [http 协议](#http协议)
*   [websocket 协议](#websocket协议)

  

__EOF__

[![](https://pic.cnblogs.com/avatar/2867340/20220506085055.png)](https://pic.cnblogs.com/avatar/2867340/20220506085055.png) *   **本文作者：** [fuminer](https://www.cnblogs.com/fuminer)
*   **本文链接：** [https://www.cnblogs.com/fuminer/p/17259291.html](https://www.cnblogs.com/fuminer/p/17259291.html)
*   **关于博主：** 发现更好的自己！
*   **版权声明：** 本博客所有文章除特别声明外，均采用 BY-NC-SA 许可协议，转载请注明出处！
*   **声援博主：** 如果您觉得文章对您有帮助，可以点击页面右下角的喜欢、关注、赞赏图标！