# Pornhub视频爬取

## 简介

众所周知，[Pornhub](http://pornhub.com/)是广大宅男宅女酷爱的网站之一：深夜逛一逛，神清气爽，祝我快速进入梦乡。

这个网站已经做得相当完善，尤其是它的关联推荐，深得我心。

由于防火墙的原因，在大陆地址不允许访问该网站。我使用[国外服务器](https://www.vultr.com/?ref=8377893-6G)搭梯子，才能勉强看到一些小视频和动图。

每次被动图诱惑得不行，但观看视频却卡得要死。对于深夜寂寞的人来说，这样的浏览无异于饮鸩止渴。

思来想去，决定还是花点时间，参考Github上其他同志的代码，做一个简单的爬虫吧。

## 爬取的板块

无论爬取视频链接还是下载视频，都会消耗梯子的流量，因此我没有深入研究这部分。

本程序仅提供[评分最高(TopRated)](https://www.pornhub.com/video?o=tr)页面的所有视频链接提取。

## 使用方法

```shell script
# 确认Python版本为Python3
python3 --version
root@adultfree:~/pornhub# python3 --version
Python 3.5.2
# 安装依赖包
root@adultfree:~/pornhub# python3 -m pip install -r requirements.txt
......
# 开始爬取亚洲BT
root@adultfree:~/pornhub# scrapy crawl top_rated
```

## 注意事项

注意pornhub/settings.py中的该选项

```python
# 当DOWNLOAD_VIDEO设为True时，程序会视图下载电影
# 在大陆地区下载速度非常慢，因此强烈建议仅获取地址
# 将地址批量拷贝，放入迅雷中下载，速度会快很多
DOWNLOAD_VIDEO = False
```

默认情况下，只会把爬取到的视频以INFO的形式保存在文件中。
打开文件，选中并复制所有带“下载地址”的行。再打开迅雷，新建任务，粘贴即可开始迅雷批量下载。
你也可以选择注释`LOG_FILE`那一行，这样打出的结果会直接打印到屏幕上。

另外，我仅提取了画质最高的版本链接。毕竟越清晰，就越真实 :-)

## 效果展示

#### 爬取结果

![爬取结果](https://raw.githubusercontent.com/adultfree/pornhub/master/images/crawl_result.png)

#### 下载状态

![下载状态](https://raw.githubusercontent.com/adultfree/pornhub/master/images/download_state.png)

## 补充说明

如果发现爬虫无法爬取信息，那应该是因为没有使用翻墙工具。

我使用的是Vultr提供的服务器，自己搭建的ShadowSocks环境。如果上图所示，网速大概能达到3MB/s，基本能应付我日常的享用。

目前价格是$5/month，大概就是一个月35块钱。目前它的网站在搞活动，对推荐Vultr的人进行奖励，有两种方式。
* 推荐一个人，获得$10(被推荐人至少消费$10) -> [点击注册](https://www.vultr.com/?ref=7567000)
* 推荐一个人，获得$25(被推荐人至少消费$25)，好处是被推荐人可以获得$100体验券($100仅1个月内有效) -> [点击注册](https://www.vultr.com/?ref=8377893-6G)

如果您注册了以上链接，并满足最小金额，我就可以获得不小的奖励~~谢谢大家