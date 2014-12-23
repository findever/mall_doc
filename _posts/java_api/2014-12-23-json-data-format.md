---
layout: post
title: 返回json数据规范
category: java_api
author: "findever"
---

__描述前端ajax请求后端java时返回的json数据格式__
<!--more-->
* 返回结果示例  
	`{status:0,data:{....},msg:"请求成功"}`

* 返回结果参数说明
	1. `status` (必须) 描述请求的状态  
	| **值范围** | **表达意义** | **备注** |  
	| 等于0 | 请求成功 | 只有此时msg参数才不是必须的 |  
	| 大于0 | 应用错误 | 其他的应用错误，与当前请求相关，如支付时余额不足等 |  
	| 小于0 | 系统错误 | 如未登录等（-1值固定为未登录/登录超时错误） |  

	2. `data` (status为0时必须) 返回的json数据
	3. `msg` (status不为0时必须) 错误提示信息