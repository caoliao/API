# API对接数据结构(初稿)

# 数据表列表数据结构

## 输入参数

|名称|类型|说明|内容示例|
|:----|:----|:----|:----|
|token|string|token 用户通过授权方式获得，用于调取数据的凭证|dcf5500c7e53721d4b016e4793d5dd66|


## 输出参数

|名称|类型|说明|内容示例|
|:----|:----|:----|:----|
|table_name|string|表名|table_D1|
|alias_table_name|string|别名|巡检记录单|

## 数据示例

```
[
  {
    "table_name": "table_D1",
    "alias_table_name": "巡检记录单",
  },
  {
    "table_name": "base_codeinfo",
    "alias_table_name": "二维码基础信息表"
  },
  {
    "table_name": "base_authmsg",
    "alias_table_name": "填表人信息表"
  }
]
```

# 数据表数据结构

`每次最多输入3000行，超过3000行，需分页接收`

`字段数量及名称，部份由用户设置决定，可能同步数据时，字段名及数量，会产生变化`

## 输入参数

|名称|类型|说明|内容示例|
|:----|:----|:----|:----|
|table_name|string|表名|table_D1|
|p|int|分页|1|
|token|string|token|dcf5500c7e53721d4b016e4793d5dd66|

## 输出参数

|名称|类型|说明|内容示例|
|:----|:----|:----|:----|
|table_name|string|表名|table_D1|
|alias_table_name|string|别名|巡检记录单|
|fields|array|字段列表|    |
|field_name|string|字段名|21368|
|alias|string|字段别名|时间|
|values|array|`值列表，每次最多返回3000行`|    |
|has_more|int|`是否有更多，1，有更多；0，当前已经返回全部内容`|0|
|p|int|当前分页，输入参数中的p的值|1|

## 数据示例
```
{
  "table_name": "table_D1",
  "alias_table_name": "巡检记录单",
  "fields": [
    {
      "field_name": "record_id",
      "alias": "record_id"
    },
    {
      "field_name": "code_id",
      "alias": "code_id"
    },
    {
      "field_name": "tpl_code_id",
      "alias": "tpl_code_id"
    },
    {
      "field_name": "code_name",
      "alias": "码名称"
    },
    {
      "field_name": "tpl_id",
      "alias": "tpl_id"
    },
    {
      "field_name": "tpl_name",
      "alias": "表单名称"
    },
    {
      "field_name": "add_time",
      "alias": "add_time"
    },
    {
      "field_name": "owner_tpl_number",
      "alias": "owner_tpl_number"
    },
    {
      "field_name": "member_id",
      "alias": "member_id"
    },
    {
      "field_name": "status",
      "alias": "状态"
    },
    {
      "field_name": "21364",
      "alias": "单行文本"
    },
    {
      "field_name": "21365",
      "alias": "多行文本"
    },
    {
      "field_name": "21366",
      "alias": "数字"
    },
    {
      "field_name": "21367",
      "alias": "日期"
    },
    {
      "field_name": "21368",
      "alias": "时间"
    },
    {
      "field_name": "21369",
      "alias": "单选项"
    },
    {
      "field_name": "21370",
      "alias": "多选项"
    },
    {
      "field_name": "21371",
      "alias": "检查项_检查项1"
    },
    {
      "field_name": "21372",
      "alias": "检查项_检查项2"
    },
    {
      "field_name": "21373",
      "alias": "定位"
    },
    {
      "field_name": "21374",
      "alias": "地址"
    },
    {
      "field_name": "21375_1312",
      "alias": "表格_项目1"
    },
    {
      "field_name": "21375_1313",
      "alias": "表格_项目2"
    },
    {
      "field_name": "21377",
      "alias": "多级选择"
    },
    {
      "field_name": "21378",
      "alias": "手写签名"
    },
    {
      "field_name": "21379",
      "alias": "图片"
    },
    {
      "field_name": "21380",
      "alias": "录音"
    },
    {
      "field_name": "21381",
      "alias": "视频"
    },
    {
      "field_name": "21382",
      "alias": "微信名"
    },
    {
      "field_name": "21383",
      "alias": "姓名"
    },
    {
      "field_name": "21383",
      "alias": "工号"
    },
    {
      "field_name": "21383",
      "alias": "手机"
    },
    {
      "field_name": "21384",
      "alias": "身份证号"
    },
    {
      "field_name": "21385",
      "alias": "车牌"
    },
    {
      "field_name": "21386",
      "alias": "性别"
    },
    {
      "field_name": "21386",
      "alias": "编号"
    }
  ],
  "values": [
    [
      128932212, 
      34782912, 
      34782912, 
      "一号楼巡检", 
      258231,
      "巡检记录单",
      "2020-04-07 12:34",
      "D1",
      6411172,
      "正常",
      "这是一个单选文本",
      "这是多行文本第一行\n这是多行文本第二行",
      "21364",
      "2020-04-07",
      "03:02",
      "选项1",
      "选项1,选项2",
      "1",
      "2",
      "浙江省宁波市海曙区后河巷17号(先进制造业公共培训平台-B座西南51米)",
      "河北省秦皇岛市北戴河区悦心花园6#808", "表格1", "表格2", "浙江省\/宁波市\/海曙区\/学校2",
      "https:\/\/ncstatic.clewm.net\/rsrc\/2020\/0407\/16\/eeb403e1eabbb0ba43d16ccad308907c.png?x-oss-process=image\/rotate,270",
      "https:\/\/ncstatic.clewm.net\/rsrc\/2020\/0407\/16\/17bb81085ad1c35c53a37624aad30c27.jpg",
      "https:\/\/tcview-nc.clewm.net\/dd5507d7d4aec18dfbb90df7a9660a5e.mp3?sign=57f604295f52fbe86887d00cf8e38c78&t=1586247450",
      "https:\/\/tcview-nc.clewm.net\/a08972fd6719fcc4885364b33c4483e5.mp4?sign=e811f4a6f0983bb70a91d7a221cac5d5&t=1586247450",
      "布朗",
      "布朗",
      "100857",
      "13486478447",
      "342564197605210854",
      "浙BRE9E3",
      "男",
      "123"
    ]
  ]
}
```
