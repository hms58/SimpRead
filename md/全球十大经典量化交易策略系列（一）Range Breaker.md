> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [mp.weixin.qq.com](https://mp.weixin.qq.com/s?__biz=MzI1NDY4Njg3Nw==&mid=2247489655&idx=1&sn=4c72858a50ae29b306d2632f0d192503&chksm=e855799740064213a926ec51a3dddc9bd0bd94f7ce4b65b406149d98d06012dfcd093306ae34#rd)

![](https://mmbiz.qpic.cn/mmbiz_png/GqS3mZcJykX3Piabpz8ySlcRicXBsHPLS5iaUsiaWr1LmOAv5MO5NdGvFt1tg3E0kib2X8q1toXQic7tesSBcEsVhhCw/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/bGCicnvSI7ZST2DC0AVG5xTvqRDzK1UCcia5eaEPyv2xPupTjK5Vs05Ax021ibFHeDBWxibm3xqtSEXFoQsJkORHrA/640?wx_fmt=png)

**量化交易**在近几年的国内期货市场上得到了飞跃式的发展，是国际市场常用的交易方式。国外量化交易的应用领域非常广泛，主要有组合管理、套利交易、趋势交易及其他量化策略等。尽管国外市场上的交易系统名称举不胜举，但经过历史检验的，才能被称为经典的**量化交易策略**。本系列推出全球前十大经典量化策略，供大家参考，以帮助大家早日形成自己的交易系统。

![](https://mmbiz.qpic.cn/mmbiz_png/7vBu6OIvS5MqCqrfIrt8m9PqCAwIOKsoIibkg9ERXOT2hAm60YmwmoiatImzxBVFvjcptuNWwmGmAvPEhvXzibwfw/640?wx_fmt=png)

前十大 S&P 交易系统排名

![](https://mmbiz.qpic.cn/mmbiz_png/6xLlCibAjMqktUAjibaEskVjZIXHgLWVA6afFl5kyic3v1zCzWpbXawPN2uEZDPWoQmzfPSjB4U7ZlYwzVIO1j9mA/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/7vBu6OIvS5MqCqrfIrt8m9PqCAwIOKsoIibkg9ERXOT2hAm60YmwmoiatImzxBVFvjcptuNWwmGmAvPEhvXzibwfw/640?wx_fmt=png)

前十大一致性最好的交易系统

![](https://mmbiz.qpic.cn/mmbiz_png/6xLlCibAjMqktUAjibaEskVjZIXHgLWVA6wBJGmWvJSjnmtw3fuIB0Kxr2LMOhIFCMYn97LU4iag0mzcgHVzpMSkg/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/GqS3mZcJykX3Piabpz8ySlcRicXBsHPLS5iaUsiaWr1LmOAv5MO5NdGvFt1tg3E0kib2X8q1toXQic7tesSBcEsVhhCw/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/bGCicnvSI7ZST2DC0AVG5xTvqRDzK1UCcia5eaEPyv2xPupTjK5Vs05Ax021ibFHeDBWxibm3xqtSEXFoQsJkORHrA/640?wx_fmt=png)

本次先介绍 **Range Breaker**（简称 R Breaker）策略，这是一种日内回转交易策略，属于短线交易，比较适合日内 1-Min 和 5-Min 级别的数据，尤其在标普 500 股指期货上效果最佳。R Breaker 策略于 1994 年公开发布，起初专用于对冲，后来延展到波段。曾**连续 15 年**荣登权威量化杂志《Futures Truth Magazine》**Top10 最赚钱策略**。

![](https://mmbiz.qpic.cn/mmbiz_png/6xLlCibAjMqktUAjibaEskVjZIXHgLWVA6a1vWBvgHmKUbXfyBg1kPcJMlwHTgeCNsFptrIZKPy9bzWRyzshd2xQ/640?wx_fmt=png)

01

原理

![](https://mmbiz.qpic.cn/mmbiz_gif/pKCA7MURrtqZdjee36Owa2jzQomEdJnc8OFZuV8sqicianha3eW7vWIS3oMVECYicIo3YFfUyHOWMVNx8X2G5GqRQ/640?wx_fmt=gif)

![](https://mmbiz.qpic.cn/mmbiz_png/GqS3mZcJykX3Piabpz8ySlcRicXBsHPLS5iaUsiaWr1LmOAv5MO5NdGvFt1tg3E0kib2X8q1toXQic7tesSBcEsVhhCw/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/bGCicnvSI7ZST2DC0AVG5xTvqRDzK1UCcia5eaEPyv2xPupTjK5Vs05Ax021ibFHeDBWxibm3xqtSEXFoQsJkORHrA/640?wx_fmt=png)

R Breaker 主要分为分为反转和趋势两部分，空仓时进行趋势跟随，持仓时等待反转信号反向开仓。反转和趋势突破的价位点根据前一交易日的收盘价 C、最高价 H 和最低价 L 计算得出，分别为：突破买入价、观察卖出价、反转卖出价、反转买入价、观察买入价和突破卖出价。

计算方法如下：  

![](https://mmbiz.qpic.cn/mmbiz_png/6xLlCibAjMqktUAjibaEskVjZIXHgLWVA6yKCibGibsg66c8C61DtbzYgj6RaE3HiaO6JmjFdTkpwtSfU4HSibia1iatdA/640?wx_fmt=png)  

02

触发条件

![](https://mmbiz.qpic.cn/mmbiz_gif/pKCA7MURrtqZdjee36Owa2jzQomEdJnc8OFZuV8sqicianha3eW7vWIS3oMVECYicIo3YFfUyHOWMVNx8X2G5GqRQ/640?wx_fmt=gif)

![](https://mmbiz.qpic.cn/mmbiz_png/GqS3mZcJykX3Piabpz8ySlcRicXBsHPLS5iaUsiaWr1LmOAv5MO5NdGvFt1tg3E0kib2X8q1toXQic7tesSBcEsVhhCw/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/bGCicnvSI7ZST2DC0AVG5xTvqRDzK1UCcia5eaEPyv2xPupTjK5Vs05Ax021ibFHeDBWxibm3xqtSEXFoQsJkORHrA/640?wx_fmt=png)

**空仓时：突破策略**  

空仓时，当盘中价格 > 突破买入价，则认为上涨的趋势还会继续，开仓做多；

空仓时，当盘中价格 < 突破卖出价，则认为下跌的趋势还会继续，开仓做空。

**持仓时：反转策略**

持多单时：当日内最高价 > 观察卖出价后，盘中价格回落，跌破反转卖出价构成的支撑线时，采取反转策略，即做空；

持空单时：当日内最低价 < 观察买入价后，盘中价格反弹，超过反转买入价构成的阻力线时，采取反转策略，即做多。

如下图所示：

![](https://mmbiz.qpic.cn/mmbiz_png/6xLlCibAjMqktUAjibaEskVjZIXHgLWVA6OgxycnS9W40DjSlfdNLLDl7V3KfVPMMcJUyUrKjNSj17XEy1kC4Gng/640?wx_fmt=png)

03

策略逻辑  

![](https://mmbiz.qpic.cn/mmbiz_gif/pKCA7MURrtqZdjee36Owa2jzQomEdJnc8OFZuV8sqicianha3eW7vWIS3oMVECYicIo3YFfUyHOWMVNx8X2G5GqRQ/640?wx_fmt=gif)

![](https://mmbiz.qpic.cn/mmbiz_png/GqS3mZcJykX3Piabpz8ySlcRicXBsHPLS5iaUsiaWr1LmOAv5MO5NdGvFt1tg3E0kib2X8q1toXQic7tesSBcEsVhhCw/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/bGCicnvSI7ZST2DC0AVG5xTvqRDzK1UCcia5eaEPyv2xPupTjK5Vs05Ax021ibFHeDBWxibm3xqtSEXFoQsJkORHrA/640?wx_fmt=png)

第一步：根据收盘价、最高价和最低价数据计算六个价位。

第二步：如果是空仓条件下，如果价格超过突破买入价，则开多仓；如果价格跌破突破卖出价，则开空仓。

第三步：在持仓条件下:

持多单时，当最高价超过观察卖出价，盘中价格进一步跌破反转卖出价，反手做多；

持空单时，当最低价低于观察买入价，盘中价格进一步超过反转买入价，反手做空。

第四步：接近收盘时，全部平仓。

04

策略历史数据回测结果  

![](https://mmbiz.qpic.cn/mmbiz_gif/pKCA7MURrtqZdjee36Owa2jzQomEdJnc8OFZuV8sqicianha3eW7vWIS3oMVECYicIo3YFfUyHOWMVNx8X2G5GqRQ/640?wx_fmt=gif)

![](https://mmbiz.qpic.cn/mmbiz_png/6xLlCibAjMqktUAjibaEskVjZIXHgLWVA6cVWfezyU79vRViaEKvKEtHQaz74paKdhREKI1N6HIic58ia2KukL0S8dQ/640?wx_fmt=png)

![](https://mmbiz.qpic.cn/mmbiz_png/7vBu6OIvS5MqCqrfIrt8m9PqCAwIOKsoIibkg9ERXOT2hAm60YmwmoiatImzxBVFvjcptuNWwmGmAvPEhvXzibwfw/640?wx_fmt=png)

历史数据回测累计收益走势图

![](https://mmbiz.qpic.cn/mmbiz_png/6xLlCibAjMqktUAjibaEskVjZIXHgLWVA6cpMhh24tMZBDPAfFhNmZrtsIRM1ClndsicpPyaVfOlYroHOTdRnqfnw/640?wx_fmt=png)

免责声明：

本文所有数据及其结论仅供研究探讨，并不构成任何交易招揽或邀约，不涉及任何操作建议。投资附带风险，过去的行情表现并不代表将来的表现，买卖金融衍生品时，随时都可能产生损失。因此请您保持谨慎思考，并在必要时咨询独立专业人士意见。中金汇理资产管理 (香港) 有限公司特此声明。

![](https://mmbiz.qpic.cn/mmbiz_png/nxYUjbjviaRkNhEtSw8J7NBlKgic2fAEZibGKrZg1kYAbvAqTlsjk9jrCaK8OH74vlQJibsTsoBGRhlZj5Sic62uVWw/640?wx_fmt=png)

**中金汇理资产管理 (香港) 有限公司**  

香港湾仔港湾径 26 号华润大厦 34 楼 3408 室  
电话: 18420676099(微信客服同号); (852)38417690

公众号：中金汇理香港 电邮: hk02@sinoif.com