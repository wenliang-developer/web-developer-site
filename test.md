###创建小包订单（中国出口）
####接口说明
新增ISP订单,仅支持单个新增。
####使用场景
卖家创建ISP订单。
####Action
isp.order.createOrder
####请求示例
```json
{
    "action": "isp.order.createOrder",
    "app_key": "rebecca",
    "client_id": "ODJKMDU1YZCTYJQ5YY00ZWZLLTK5N2QTOWY4MZI5OGMWNDG2",
    "client_sign": "DFF0A6FC0AFDB044ED19E7C213C9D3BB",
    "data": {
        "winitProductCode": "WP-MYP002",
        "dispatchType": "S",
        "shipperAddrCode": "test110",
        "warehouseCode": "YW10000009",
        "refNo": "卖家订单号",
        "ebaySellerId": "bessky_cn",
        "isAllowRepeat": "Y",
        "vatNo": "GB123456789",
         "iossNo": "",
        "eoriNo": "GB012345678912",
        "pickUpCode": "123testremark",
         "buyerCompany":"",
        "buyerCountry": "US",
        "buyerState": "HI",
        "buyerCity": "Honolulu",
        "buyerZipCode": "96816-3343",
        "buyerEmail": "abc@winit.com.cn",
        "buyerName": "COCO",
        "buyerContactNo": "13800001111",
        "buyerHouseNo": "1",
        "recipientTaxID": "",
        "buyerAddress1": "3944 Sierra Dr",
        "buyerAddress2": "",
        "packageList": [
            {
                "length": "2",
                "width": "1.23",
                "height": "1.23",
                "weight": "1.23",
                "merchandiseList": [
                    {
                        "merchandiseCode": "IPhone X",
                        "declaredNameCn": "苹果手机12345",
                        "declaredNameEn": "ihpone",
                        "declaredValue": "10.23",
                        "hsCode": "3924100090",
                        "itemID": "110",
                        "transactionID": "1234567890",
                        "merchandiseQuantity": "2",
                        "goodsLocation": "测试库存"
                    }
                ]
            }
        ]
    },
    "format": "json",
    "language": "zh_CN",
    "platform": "OWNERERP",
    "sign": "B60D8C0AA9598A91F041968D5971A0E1",
    "sign_method": "md5",
    "timestamp": "2016-03-22 19:26:41",
    "version": "1.0"
}
```
####返回示例
```json
{
   "code": "0",
   "msg": "操作成功",
   "data":    {
      "orderNo": "ID15270000000487ZZ",
      "trackingNo": "AT06031845335CN"
   }
```
####请求入参
|名称|类型|必填|说明|示例<br>沙箱环境|
|-----|-----|-----|-----|------|
|refNo|String(60)|N|卖家订单号||
|isAllowRepeat|String(60)|N|是否允许卖家订单号重复可选:<br>Y:允许重复<br>N:不允许重复<br>不填为允许重复||
|winitProductCode|String(60)|Y|winit产品编码获取方法:<br>(1)接口调用查询小包物流渠道接口或者获得productCode<br>(2)卖家填入||
|dispatchType|String(1)|Y|发货方式<br>P:Winit揽收<br>S:自发快递<br>T:卖家自送<br>C:中邮揽收（停用）<br>D:DHL揽收（停用）||
|warehouseCode|String(10)|Y|验货仓Code<br>获取方法：<br>(1)通过接口调用查询国内验货仓接口获得warehouseCode<br>(2)卖家填入||
|shipperAddrCode|String(8)|Y|寄件人地址Code获取方法<br>(1)通过接口调用查询提货地址接口获得code<br>（2）卖家填入||
|vatNo|String(128)|N|发件人税号<br>支持填写发件人VAT||
|iossNo|String(128)|O|IOSS<br>选填，按PSC要求填写||
|eoriNo|String(128)|N|发件人EORI||
|ebaySellerId|String(60)|O|ebay卖家ID||
|eBay订单必填|||||
|pickUpCode|String(50)|N|捡货条码/备注条码||
|buyerCompany|String(50)|N|收件人公司||
|buyerCountry|String(50)|Y|收件人国家||
|buyerState|String(20)|Y|收件人州||
|buyerCity|String(50)|Y|收件人城市||
|buyerZipCode|String(10)|Y|收件人邮编||
|buyerEmail|String(60)|N|收件人邮箱||
|buyerName|String(50)|Y|收件人名字||
|buyerContactNo|String(20)|Y|收件人电话||``
|buyerHouseNo|String(10)|N|收件人门牌号||
|recipientTaxID|String(64)|N|收件人税号||
|buyerAddress1|String(100)|Y|收件人地址1||
|buyerAddress2|String(100)|N|收件人地址2||
|packageList|Array||包裹列表,以下字段为packageList子节点||
|--length|Numeric(4,2)|Y|长(CM)||
|--width|Numeric(4,2)|Y|宽(CM)||
|--height|Numeric(4,2)|Y|高(CM)||
|--weight|Numeric(4,6)|Y|总重量/包裹总量（KG）||
|--trackingNo|String(60)|O|第三方跟踪号<br>小包正常下单可以不填写||
|-merchandiseList||Y|商品列表,以下字段为merchandiseList子节点||
|--merchandiseCode|String(100)|N|商品sku|配货单|
|--declaredNameCn|String(100)|Y|申报品名(中文)||
|--declaredNameEn|String(100)|Y|申报品名(英文)||
|--declaredValue|Numeric(8,2)|Y|单个商品申报价格(USD)||
|--hsCode|String(32)|O|海关申报编码||
                
####返回出参
|名称|类型|必填|说明|示例<br>沙箱环境|
|-----|-----|-----|-----|------|
|refNo|String(60)|N|卖家订单号||
|orderNo|String(60)|Y|ISP 订单号||
|trackingNo|String(60)|Y|跟踪号||
                
####常用工具
####常见问题

``
