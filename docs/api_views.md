# 后端API接口说明
> 部分echarts获取展示的数据是通过请求后端的api接口获取，而不是由Django模板渲染而来，方便代码复用

---

## download
- URL：http://100.100.0.177/api/files/download
- 功能：下载服务器上的文件
- 请求类型：GET
- 请求参数：

参数 | 是否必须 | 说明
-|-|-
filename | 必须 | 附件文件名

- 请求示例：http://100.100.0.177/api/files/download?filename=基金创投公司风险指标.xlsx
- 返回值：无

## avg_problem_percentage
- URL：http://100.100.0.177/api/dashboard/avg_problem_percentage
- 功能：获取所有季度的各公司平均问题占比
- 请求类型：GET
- 请求参数：无
- 返回值：
```
[
	["quarter", "2019Q1", "2019Q2", "2019Q3", "2019Q4"],
	["粤财信托", "4.55", "1.35", "0.00", "0.00"],
	["粤财资产", "4.38", "4.34", "0.00", "0.00"],
	["广东再担保", "14.40", "14.02", "0.00", "0.00"],
	["粤财金科", "0.00", "0.00", "0.00", "0.00"],
	["基金创投", "86.14", "77.15", "0.00", "0.00"],
	["中银粤财", "73.70", "32.37", "0.00", "0.00"],
	["金租", "5.98", "13.76", "13.72", "13.72"]
]
```

---

## same_problem_top5
- URL：http://100.100.0.177/api/dashboard/same_problem_top5
- 功能：获取指定季度的各公司同类问题Top 5统计
- 请求类型：GET
- 请求参数：

参数 | 是否必须 | 说明
-|-|-
quarter | 必须 | 指定季度获取数据

- 返回值：
```
{
	"name": ["交易本金金额", "机构证件号码", "机构证件类别", "项目名称", "其他"],
	"value": ["6.84", "49.28", "48.84", "4.34", 224.8]
}
```

---

## subcompany_data_percentage
- URL：http://100.100.0.177/api/dashboard/subcompany_data_percentage
- 功能：获取指定季度的各公司数据量占比
- 请求类型：GET
- 请求参数：

参数 | 是否必须 | 说明
-|-|-
quarter | 必须 | 指定季度获取数据

- 返回值：
```
[{
	"name": "粤财信托",
	"value": "6195905"
}, {
	"name": "粤财资产",
	"value": "72575"
}, {
	"name": "广东再担保",
	"value": "11892"
}, {
	"name": "粤财金科",
	"value": "33792215"
}, {
	"name": "基金创投",
	"value": "397"
}, {
	"name": "中银粤财",
	"value": "945"
}, {
	"name": "金租",
	"value": "67"
}]
```
---
## count_db_rows
- URL：http://100.100.0.177/api/dashboard/count_db_rows
- 功能：获取指定季度的统计各类数据库数据量
- 请求类型：GET
- 请求参数：

参数 | 是否必须 | 说明
-|-|-
quarter | 必须 | 指定季度获取数据

- 返回值：
```
[{
	"name": "MySQL",
	"value": "33804107",
	"selected": "true"
}, {
	"name": "Oracle",
	"value": "72642"
}, {
	"name": "SQL server",
	"value": "1333"
}]
```
---

## data_overiew
- URL：http://100.100.0.177/api/dashboard/data_overiew
- 功能：获取指定季度的统计风险集市相关 总数据量、总问题数据量、总问题占比
- 请求类型：GET
- 请求参数：

参数 | 是否必须 | 说明
-|-|-
quarter | 必须 | 指定季度获取数据

- 返回值：
```
{
	"all_cnt": "205952332",
	"problem_cnt": "1423787",
	"problem_per": "0.69"
}
```

---

## total_trend
- URL：http://100.100.0.177/api/dashboard/total_trend
- 功能：获取所有季度的显示集团总问题占比走势
- 请求类型：GET
- 请求参数：无
- 返回值：
```
{
	"quarter": ["2019Q1", "2019Q2", "2019Q3", "2019Q4"],
	"value": ["0.69", "0.88", "0.00", "0.00"]
}
```