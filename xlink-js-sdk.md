# JS SDK �ӿ��ĵ� #
������ΪH5�����ṩ�˿�ƽ̨(android ios)�������ӿ�JS SDK(���¼��JS SDK)��֧��WIFI������ģʽ���ӡ�


- [����](#overview)
- [��װ����](#installation)
- [����ʾ��](#example)
- [�ӿ��ĵ�](#document)

## <a name='overview'>����</a> ##
���ĵ�������JS SDK�İ�װ��ʹ�÷����������򵥵Ĵ���ʾ��
JS SDK�ṩ��2����:'XSDK'��'Device'��[ͼ1.1](#uml)��JS SDK��UML��ͼ
![ͼ1.1]()

## <a name='installation'>��װ����</a> ##
## <a name='example'>����ʾ��</a> ##
## <a name='document'>�ӿ��ĵ�</a> ##
### <a name='xsdk'>Class XSDK</a> ###
JS SDK ��window�±�¶��һ��ȫ�ֵ�XSDK�࣬���ݹ��캯�����������ز�ͬ������ʵ����ÿ�����ӣ���������WIFI��ֻά��һ��ʵ����XSDK���ṩ����([UI](#xui) [���ݴ洢](#dataStorage))�Ⱦ�̬������

#### ���� ####
| ���η������� | ���Ժ����� |
|--------------|------------|
| String | sdkType (ʵ�������ͣ���������WIFI) |
| Array | devices (Device��������) |
| static Object | systemInfo (����ϵͳ��������Ϣ) |
| [XUI](#xui) | ui (UI��ز����࣬����رմ��ڣ�ɨ���ά��) |
| [DataStorage](#dataStorage) | dataStorage (���ݴ洢) |

#### ���캯�� ####
| ���η������� | ���캯�������� |
|--------------|------------|
| [XSDK](#xsdk) | XSDK(String type) (����XSDK��һ������ʵ��) <br/>������type-�豸����[SDKType](#sdkType)��һ��|

#### ���� ####
| ���η������� | ���������� |
|--------------|------------|
| void | emit (String event) (�����¼�) <br/> ����: event-֧�ֵķ����¼���[STARTSCAN](#STARTSCAN) [CANCELSCAN](#CANCELSCAN) [DESTORY](#DESTORY)|
| void | on (String event, Function cb) (�����¼�) <br/>����: event-֧�ֵļ����¼���[READY](#READY) [SCAN](#DISCONNECT) [DATA](#DATA) [TIMEOUT](#TIMEOUT) [ERROR](#ERROR) <br/> &#8195;&#8195;&#8195;cb-�����¼��Ļص�����|

### <a name='device'>Class Device</a> ###
Device���ʾ�豸��ÿһ��Deviceʵ�������豸id(device_id)Ψһ����һ���豸��
#### ���� ####
| ���η������� | ���Ժ����� |
|--------------|------------|
| String | id (�豸id) |

#### ���캯�� ####
| ���η������� | ���캯�������� |
|--------------|------------|
| [Device](#device) | Device(String id) (�����豸ʵ��) <br/> ������id-�豸id|

#### ���� ####
| ���η������� | ���������� |
|--------------|------------|
| void | emit (String event[, String data]) (�����¼�) <br/> ����: event-֧�ֵķ����¼���[CONNECT](#CONNECT) [DISCONNECT](#DISCONNECT) [GET](#GET) [PUT](#PUT)<br/>&#8195;&#8195;&#8195;data-�����¼�Ϊ[PUT](#PUT)ʱ���|
| void | on (String event, Function cb) (�����¼�) <br/>����: event-֧�ֵļ����¼���[CONNECT](#CONNECT) [DISCONNECT](#DISCONNECT) [DATA](#DATA) [TIMEOUT](#TIMEOUT) [ERROR](#ERROR) <br/> &#8195;&#8195;&#8195;cb-�����¼��Ļص�����|

### Class SDKEvent ###
#### ���� ####
| ���η������� | ���Ժ����� |
|--------------|------------|
| const String | <a name='CONNECT'>CONNECT</a> (�����豸) |
| const String | <a name='DISCONNECT'>DISCONNECT</a> (�Ͽ��豸����) |
| const String | <a name='DATA'>DATA</a> (�豸���ݸ���) |
| const String | <a name='GET'>GET</a> (��ȡ�豸����) |
| const String | <a name='PUT'>PUT</a> (�����豸����) |
| const String | <a name='READY'>READY</a> (SDK ����������ɨ���豸) |
| const String | <a name='STARTSCAN'>STARTSCAN</a> (��ʼɨ���豸) |
| const String | <a name='CANCELSCAN'>CANCELSCAN</a> (ȡ��ɨ���豸) |
| const String | <a name='SCAN'>SCAN</a> (ɨ���豸���) |
| const String | <a name='DESTORY'>DESTORY</a> (����һ������ʵ��) |
| const String | <a name='TIMEOUT'>TIMEOUT</a> (��ʱ) |
| const String | <a name='ERROR'>ERROR</a> |

### <a name='sdkType'>Class SDKType</a> ###
#### ���� ####
| ���η������� | ���Ժ����� |
|--------------|------------|
| const String | WIFI |
| const String | BLUETOOTH |

### <a name='xui'>Class XUI</a> ###
#### ���� ####
| ���η������� | ���������� |
|--------------|------------|
### <a name='dataStorage'>Class DataStorage</a> ###
#### ���� ####
| ���η������� | ���������� |
|--------------|------------|
| Boolean | put(String key, String value) |
| String | get(String key) |