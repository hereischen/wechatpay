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

API
---

To donwload bill of 2015-07-26, call:
 a = DownloadBill().get_bill('2015-07-26')
