# JS SDK 接口文档 #
云智易为H5开发提供了跨平台(android ios)的容器接口JS SDK(以下简称JS SDK)，支持WIFI和蓝牙模式连接。


- [概述](#overview)
- [安装方法](#installation)
- [代码示例](#example)
- [接口文档](#document)

## <a name='overview'>概述</a> ##
该文档描述了JS SDK的安装和使用方法。包括简单的代码示例
JS SDK提供了2个类:'XSDK'和'Device'。[图1.1](#uml)是JS SDK的UML类图
![图1.1](https://github.com/ShighGoing/Interface/blob/master/resource/image/xjssdk.png)

## <a name='installation'>安装方法</a> ##
## <a name='example'>代码示例</a> ##
## <a name='document'>接口文档</a> ##
### <a name='xsdk'>Class XSDK</a> ###
JS SDK 在window下暴露了一个全局的XSDK类，根据构造函数参数，返回不同的连接实例，每个连接（蓝牙或者WIFI）只维护一个实例。XSDK还提供包括([UI](#xui) [数据存储](#dataStorage))等静态方法。

#### 属性 ####
| 修饰符和类型 | 属性和描述 |
|--------------|------------|
| String | sdkType (实例的类型，蓝牙或者WIFI) |
| Array | devices (Device类型数组) |
| static Object | systemInfo (操作系统和容器信息) |
| [XUI](#xui) | ui (UI相关操作类，例如关闭窗口，扫描二维码) |
| [DataStorage](#dataStorage) | dataStorage (数据存储) |

#### 构造函数 ####
| 修饰符和类型 | 构造函数和描述 |
|--------------|------------|
| [XSDK](#xsdk) | XSDK(String type) (返回XSDK的一个连接实例) <br/>参数：type-设备类型[SDKType](#sdkType)的一种|

#### 方法 ####
| 修饰符和类型 | 方法和描述 |
|--------------|------------|
| void | emit (String event) (触发事件) <br/> 参数: event-支持的发送事件有[STARTSCAN](#STARTSCAN) [CANCELSCAN](#CANCELSCAN) [DESTORY](#DESTORY)|
| void | on (String event, Function cb) (监听事件) <br/>参数: event-支持的监听事件有[READY](#READY) [SCAN](#DISCONNECT) [DATA](#DATA) [TIMEOUT](#TIMEOUT) [ERROR](#ERROR) <br/> &#8195;&#8195;&#8195;cb-监听事件的回调函数|

### <a name='device'>Class Device</a> ###
Device类表示设备。每一个Device实例根据设备id(device_id)唯一关联一个设备。
#### 属性 ####
| 修饰符和类型 | 属性和描述 |
|--------------|------------|
| String | id (设备id) |

#### 构造函数 ####
| 修饰符和类型 | 构造函数和描述 |
|--------------|------------|
| [Device](#device) | Device(String id) (返回设备实例) <br/> 参数：id-设备id|

#### 方法 ####
| 修饰符和类型 | 方法和描述 |
|--------------|------------|
| void | emit (String event[, String data]) (触发事件) <br/> 参数: event-支持的发送事件有[CONNECT](#CONNECT) [DISCONNECT](#DISCONNECT) [GET](#GET) [PUT](#PUT)<br/>&#8195;&#8195;&#8195;data-仅在事件为[PUT](#PUT)时添加|
| void | on (String event, Function cb) (监听事件) <br/>参数: event-支持的监听事件有[CONNECT](#CONNECT) [DISCONNECT](#DISCONNECT) [DATA](#DATA) [TIMEOUT](#TIMEOUT) [ERROR](#ERROR) <br/> &#8195;&#8195;&#8195;cb-监听事件的回调函数|

### Class SDKEvent ###
#### 属性 ####
| 修饰符和类型 | 属性和描述 |
|--------------|------------|
| const String | <a name='CONNECT'>CONNECT</a> (连接设备) |
| const String | <a name='DISCONNECT'>DISCONNECT</a> (断开设备连接) |
| const String | <a name='DATA'>DATA</a> (设备数据更新) |
| const String | <a name='GET'>GET</a> (获取设备数据) |
| const String | <a name='PUT'>PUT</a> (设置设备数据) |
| const String | <a name='READY'>READY</a> (SDK 就绪，可以扫描设备) |
| const String | <a name='STARTSCAN'>STARTSCAN</a> (开始扫描设备) |
| const String | <a name='CANCELSCAN'>CANCELSCAN</a> (取消扫描设备) |
| const String | <a name='SCAN'>SCAN</a> (扫描设备完成) |
| const String | <a name='DESTORY'>DESTORY</a> (销毁一个连接实例) |
| const String | <a name='TIMEOUT'>TIMEOUT</a> (超时) |
| const String | <a name='ERROR'>ERROR</a> |

### <a name='sdkType'>Class SDKType</a> ###
#### 属性 ####
| 修饰符和类型 | 属性和描述 |
|--------------|------------|
| const String | WIFI |
| const String | BLUETOOTH |

### <a name='xui'>Class XUI</a> ###
#### 方法 ####
| 修饰符和类型 | 方法和描述 |
|--------------|------------|
### <a name='dataStorage'>Class DataStorage</a> ###
#### 方法 ####
| 修饰符和类型 | 方法和描述 |
|--------------|------------|
| Boolean | put(String key, String value) |
| String | get(String key) |

###蓝牙及WIFI内网流程图###
```flow
st=>start: Start
init=>operation: 初始化XSDK
addEventListener=>operation: 添加XSDK监听
getDevices=>operation: 扫描设备
connectDevice=>operation: 连接设备
controlDevice=>operation: 监听设备信息/向设备发送数据
deviceCond=>condition: connect or error?
sdkCond=>condition: ready or error？
e=>end: End

st->init->addEventListener->sdkCond
sdkCond(no)->e
sdkCond(yes)->getDevices->connectDevice->deviceCond
deviceCond(yes)->controlDevice
deviceCond(no)->e
```
