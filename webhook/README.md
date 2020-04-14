## 接受记录数据推送
###数据示例
```
{
	"record_id": 7414,
	"code_id": 2601923,
	"tpl_id": 4027,
	"add_time": 1586246864,
	"recorder": "123",
	"content": [{
		"id": 16912,
		"title": "单行文本",
		"type": "text",
		"value": "这是一个单选文本"
	}, {
		"id": 16913,
		"title": "多行文本",
		"type": "textarea",
		"value": "这是多行文本第一行\n这是多行文本第二行"
	}, {
		"id": 16914,
		"title": "数字",
		"type": "number",
		"value": "21364"
	}, {
		"id": 16915,
		"title": "日期",
		"type": "date",
		"value": "2020-04-07"
	}, {
		"id": 16916,
		"title": "时间",
		"type": "time",
		"value": "03:02"
	}, {
		"id": 16917,
		"title": "单选项1",
		"type": "radio",
		"value": "选项1"
	}, {
		"id": 16918,
		"title": "单选项2",
		"type": "radio",
		"value": "其他[这是单选其他]"
	}, {
		"id": 16919,
		"title": "多选项1",
		"type": "checkbox",
		"value": ["选项1", "选项2"]
	}, {
		"id": 16920,
		"title": "多选项2",
		"type": "checkbox",
		"value": ["选项1", "其他[这是多选其他]"]
	}, {
		"id": 16921,
		"title": "检查项",
		"type": "checklist",
		"value": [{
			"title": "检查项1",
			"value": "1"
		}, {
			"title": "检查项2",
			"value": "2"
		}]
	}, {
		"id": 16922,
		"title": "定位",
		"type": "address",
		"value": {
			"address": "浙江省宁波市海曙区后河巷17号(先进制造业公共培训平台-B座西南51米)",
			"lat": 29.879169921875,
			"log": 121.53221950955
		}
	}, {
		"id": 16923,
		"title": "地址",
		"type": "owner_address",
		"value": "河北省秦皇岛市北戴河区悦心花园6#808"
	}, {
		"id": 16924,
		"title": "表格",
		"type": "matrix",
		"value": [{
			"title": "项目1",
			"value": "表格1"
		}, {
			"title": "项目2",
			"value": "表格2"
		}]
	}, {
		"id": 16925,
		"title": "多级选择",
		"type": "chained_selects",
		"value": "浙江省\/宁波市\/海曙区\/学校2"
	}, {
		"id": 16926,
		"title": "手写签名",
		"type": "signature",
		"value": [{
			"url": "https:\/\/ncstatic.clewm.net\/rsrc\/2020\/0407\/16\/eeb403e1eabbb0ba43d16ccad308907c.png?x-oss-process=image\/rotate,270",
			"size": "62967",
			"is_onlocal": "0",
			"height": "289",
			"width": "716"
		}]
	}, {
		"id": 16927,
		"title": "图片",
		"type": "image",
		"value": [{
			"url": "https:\/\/ncstatic.clewm.net\/rsrc\/2020\/0407\/16\/17bb81085ad1c35c53a37624aad30c27.jpg",
			"size": "97809",
			"width": "640",
			"height": "854",
			"is_onlocal": "1"
		}, {
			"url": "https:\/\/ncstatic.clewm.net\/rsrc\/2020\/0407\/16\/cfeb5e419c9ea82dde650142ab469434.jpg",
			"size": "107365",
			"width": "640",
			"height": "854",
			"is_onlocal": "1"
		}]
	}, {
		"id": 16928,
		"title": "录音",
		"type": "audio",
		"value": [{	
			"long": 5.96,
			"size": 36.28125,
			"url": "https:\/\/tcview-nc.clewm.net\/dd5507d7d4aec18dfbb90df7a9660a5e.mp3?sign=57f604295f52fbe86887d00cf8e38c78&t=1586247450",
			"play_token": "abca256c98ec52f0cc58650c6d112ac5"
		}]
	}, {
		"id": 16929,
		"title": "视频",
		"type": "video",
		"value": [{
			"size": 109241,
			"long": 2,
			"width": 464,
			"height": 960,
			"url": "https:\/\/tcview-nc.clewm.net\/a08972fd6719fcc4885364b33c4483e5.mp4?sign=e811f4a6f0983bb70a91d7a221cac5d5&t=1586247450",
			"save_key": "free\/a08972fd6719fcc4885364b33c4483e5.mp4",
			"play_token": "14dabb3ce3616d065c0afb2c256e4f59"
		}]
	}, {
		"id": 16930,
		"title": "微信名",
		"type": "recorder",
		"value": "123"
	}, {
		"id": 16931,
		"title": "姓名",
		"type": "name",
		"value": "布朗"
	}, {
		"id": 16932,
		"title": "工号",
		"type": "job_number",
		"value": "100857"
	}, {
		"id": 16933,
		"title": "手机",
		"type": "tel",
		"value": "13486478447"
	}, {
		"id": 16934,
		"title": "身份证号",
		"type": "identity",
		"value": "342564197605210854"
	}, {
		"id": 16935,
		"title": "车牌",
		"type": "carnumber",
		"value": "浙BRE9E3"
	}, {
		"id": 16936,
		"title": "性别",
		"type": "sex",
		"option_id": 37137,
		"value": "男"
	}, {
		"id": 16937,
		"title": "编号",
		"type": "customer_number",
		"customer_components_id": 109,
		"value": "123"
	}]
}
```
### 字段说明
|参数|描述|
|:----|:---|
|record_id|记录唯一ID|
|code_id|码唯一ID|
|tpl_id|记录模板唯一ID|
|add_time|记录添加时间|
|recorder|记录人|
|content|记录内容|
|&emsp;field_id|组件唯一ID|
|&emsp;title|组件名称|
|&emsp;type|组件类型（参见类型组件类型描述）|
|&emsp;value|组件值|

###组件类型
|组件名称|组件描述|值类型|值描述|
|:----|:----|:----|:----|
|text|单行文本|文本|示例：这是一个单选文本|
|textarea|多行文本|文本|示例：这是多行文本第一行\n这是多行文本第二行|
|number|数字|数字|示例：21364|
|date|日期|日期|示例：2020-04-07|
|time|时间|时间|示例|示例：03:02|
|radio|单选|文本|示例：<br>&emsp;正常单选：选项1<br>&emsp;勾选其他：其他[这是单选其他]|
|checkbox|多选|数组|示例：<br>&emsp;正常多选：["选项1", "选项2"]<br>&emsp;勾选其他：["选项1", "其他[这是多选其他]"]|
|image|图片组件|数组|示例：[{"url":"https:\/\/ncstatic.clewm.net\/rsrc\/2020\/0407\/16\/17bb81085ad1c35c53a37624aad30c27.jpg","is_onlocal":"1"}]<br>url：图片地址<br>is_onlocal：是否现场拍摄（0否/1是）|
|checklist|检查项|数组|示例：[{"title":"检查项1","value":"1"},{"title":"检查项2","value":"2"}]<br>title：检查项名称；value：1（√）/2（✗）|
|recorder|联系人|文本|示例：记录人|
|tel|手机|手机格式|示例：13567945671|
|address|定位|数组|示例：{"address":"浙江省宁波市海曙区后河巷17号(先进制造业公共培训平台-B座西南51米)","lat":29.879169921875,"log":121.53221950955}<br>address：详细地址<br>lat/log：经纬度|
|audio|录音|数组|示例：[{"url":"https:\/\/tcview-nc.clewm.net\/dd5507d7d4aec18dfbb90df7a9660a5e.mp3"}]<br>url：音频地址|
|video|视频|数组|示例：[{"url":"https:\/\/tcview-nc.clewm.net\/a08972fd6719fcc4885364b33c4483e5.mp4"}]<br>url：视频地址|
|identity|身份证|身份证格式|示例：342564197605210854|
|owner_address|地址|文本|示例：河北省秦皇岛市北戴河区悦心花园6#808|
|carnumber|车牌号|文本|示例：浙BRE9E3|
|name|姓名|文本|示例：布朗|
|sex|性别|文本|示例：男|
|matrix|表格|数组|示例：[{"title":"项目1","value":"表格1"},{"title":"项目2","value":"表格2"}]<br>title：表格项目<br>value：表格内容|
|chained_selects|多级下拉|数组|示例：浙江省/宁波市/海曙区/学校2|
|signature|手写签名|数组|示例[{"url":"https:\/\/ncstatic.clewm.net\/rsrc\/2020\/0407\/16\/eeb403e1eabbb0ba43d16ccad308907c.png"}]<br>url：图片地址|
|customer_number|自定义部署编号|文本|示例：123|
|job_number|工号|文本|示例：100857|



