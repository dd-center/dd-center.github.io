# GitHub！DD出现了！

### 部分项目联系图:

![dependency](dependency.svg)

### 说明:

* vdb [https://github.com/bilibili-dd-center/vdb](https://github.com/bilibili-dd-center/vdb)

  Virtual Youtuber Database，一个虚拟主播的数据库

* vtbs.moe [https://github.com/bilibili-dd-center/vtbs.moe](https://github.com/bilibili-dd-center/vtbs.moe)

  * Hawk

    分析实时直播弹幕并生成词云

    1. 每分钟从`falcon`读取过去1小时与过去24小时的弹幕，然后使用`dictionary`与`nodejieba`结合分析实时直播弹幕关键词，并将结果Push给`api.vtbs.moe`

  * Snake

    1. 监听`vd`的开播与人气变化提醒，之后每15秒会Push到前端

  * api.vtbs.moe

    vtbs.moe的后端

    1. 从`vdb`更新数据库并将变化push到vtbs.moe的前端
    2. 提供访问网站level数据的公共API`/v1`
    3. 转发来自`vd`的实时弹幕并提供公共API`/vds`
    4. 每五分钟调用`bili-api`与`api.vtb.wiki`更新数据并push到vtbs.moe前端
    5. 将来自`Hawk`的词云更新Push到前端
    6. 将来自`Snake`的 人气/开播状态变化 快速反应(<15秒) Push到前端
    7. 通过`falcon`访问influxdb获取历史人气值

* bilibili-vtuber-live-danmaku-relay [https://github.com/bilibili-dd-center/bilibili-vtuber-live-danmaku-relay](https://github.com/bilibili-dd-center/bilibili-vtuber-live-danmaku-relay)

  * vd

    bilibili直播间event合并转发

    1. 通过`bilibili-live-ws`打开直播间
    2. 监听`api.vtbs.moe`，自动打开新的直播间
    3. 打开Socket.io服务器，dispatch filtered and parsed events

* dictionary [https://github.com/bilibili-dd-center/dictionary](https://github.com/bilibili-dd-center/dictionary)

  DD词典，用于分析等相关业务



## Vtuber相关项目请见 [awesome-vtuber](https://github.com/bilibili-dd-center/awesome-vtuber)

