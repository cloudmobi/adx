# adx


adx使用[openrtb-v2.5](./doc/openrtb-v2.5.pdf)并在Bid的Ext字段中做如下约定

```json
{
    "clk_url": "广告的点击链接地址",
    "final_url": "广告的落地页地址",
    "imp_tk_urls": [
        "曝光监控地址"
    ],
    "clk_tk_urls": [
        "点击监控地址"
    ]
}
```
调用`http://dev.adx.cloudmobi.net:11211/request_example`便会发送一条bid请求

请求使用post方法将信息发送给dsp

请求示例

```json
{
    "id":"1111",
    "imp":[
        {
            "id":"1111-0",
            "banner":{
                "w":19,
                "h":10
            },
            "bidfloor":0.3,
            "bidfloorcur":"USD"
        }
    ],
    "app":{
        "bundle":"com.gmedal.goldgmedal(nat0)"
    },
    "device":{
        "geo":{
            "country":"HKG"
        },
        "ip":"103.206.188.3",
        "os":"iOS",
        "h":667,
        "w":375
    },
    "at":2,
    "tmax":200,
    "cur":[
        "USD"
    ]
}
```

一个简单的示例返回

```json
{
    "id": "123",
    "bidid": "1122",
    "seatbid": [
    {
        "seat": "seat",
        "bid": [
        {
            "id": "1",
            "impid": "123456",
            "price": 1.23,
            "nurl": "http://nurl.com",
            "iurl": "http://iur/image.com",
            "ext": {
                "clk_url": "http://clkurl.com",
                "final_url": "http://finalurl.com",
                "imp_tk_urls": ["https://imptkurls.com"],
                "clk_tk_urls": ["https://clktkurls.com"]
	        }
        }]
    }]
}
```
