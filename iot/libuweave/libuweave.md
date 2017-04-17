<!-- $theme: gaia -->
<!-- page_number: true -->
# **==LIBUWEAVE==**<br/>简介
###### *duyh@haierubic.com*
###### 2017/04/17


---
# LIBUWEAVE
###### **Libuweave**是针对BLE(蓝牙低功耗版本)设计，运行在资源受限的MCU上，uWeave 设备作为一个GATT server运行，提供一个GATT Service,该Service有两个characteristic
+ TX : 客户端通过该characteristic写数据（请求）
+ RX : 客户端通过该characteristic读数据（回复)
###### Service和characteristic都有自己的UUID


---
# BLE短连接
+ ###### GATT clients 连接上uweave设备后，发送一个或多个请求并接收回复后就断开
+ ###### 断开时uweave设备会通过BLE周期性的对外广告自身，以便使客户端发现自己
+ ###### 通过短连接控制这种方式达到节电的目的



---
###### **uWeave**采用CBOR(对象编码格式)进行数据编码,CBOR被称为二进制的JSON格式，大概格式如下:
```
 0xA3,                       // {
 0x01,      0x0A,            //   api: SUBTRACT
 0x02,      0x03,            //   request_id: 3
 0x10,      0xA2,            //   api_params: {
 0x00,      0x05,            //     subtrahend: 5
 0x01,      0x08,            //     minuend: 8
                             // }}
```
###### CBOR通过MAP的方式实现同JSON的映射，详细可通过(http://cbor.io/)了解



---
# Commands and State
+ ###### uweave设备实现支持一系列commands
+ ###### command有固定的名字并且支持一个或多个参数
+ ###### client通过发送command给设备更改指定的state
+ ###### client通过轮询检测设备state变化



---
###### 由于谷歌的libuweave代码仓库已删除，网上也已经没有相关资料(weave官网现有的资料都是针对libiota的)，可以根据遗留的libuweave源码(徐彦伟很久以前下载的)得知：
+ libuweave 只针对低功耗蓝牙BLE设备
+ libuweave 没有libiota明确的trait概念和设备模型
+ libuweave 没有自动生成的代码，设备的command都是手工编码实现的



---
# **完**


