# WeChat微信支付
------

##Overview

Python-Django WeChat payment API, it contains 7 main classes:

> * UnifiedOrderPay 
> * NativeOrderPay 
> * JsAPIOrderPay
> * OrderQuery
> * Refund
> * RefundQuery
> * DownloadBill

------

Installation
------------

Install using pip:

```bash
pip install wechatpay
```

APIs
---
for latest version.
Init accounts 
------------
Account info needs to be retrieved form ChannelAccount table:
```python
list_of_wechat_accounts = ChannelAccount.objects.filter(channel=1)
for account in list_of_wechat_accounts:
     wecaht_config=WechatConfig(account.config)
```
OrderPays
------------
Three order pays are similar.
* UnifiedOrderPay 
* NativeOrderPay 
* JsAPIOrderPay
For example:

```python
from wechatpay.wechatpay import (NativeOrderPay as 
                                WeChatNativePayRequest,
                                OrderQuery as WeChatOrderQuery)
                                
def get_channel_account_config_dict(trade):
    order = trade.order_set.first()
    seller = Seller.objects.get_seller(order.sys_code, order.channel, order.seller_id)

    config = {}
    for (k, v) in seller.channel_account.config.items():
        config[str(k)] = str(v)

    return config

                                
pay_request = WeChatNativePayRequest(WechatConfig(get_channel_account_config_dict(trade)))
```


DownloadBill
------------
To donwload bills of date '2015-07-26' of multiple wechat accounts , based on your data structure, init corresponding accounts info and call get_bill():
```python
list_of_wechat_accounts = ChannelAccount.objects.filter(channel=1)
for account in list_of_wechat_accounts:
     DownloadBill(WechatConfig(account.config)).get_bill('2015-10-15')
```


------