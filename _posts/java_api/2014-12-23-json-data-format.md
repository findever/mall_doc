---
layout: post
title: 返回json数据规范
category: java_api
author: "findever"
---

__描述前端ajax请求后端java时返回的json数据格式__

<!--more-->

* 返回结果示例  
{% highlight json %}
	{status:"logined", "secret":0, data:{"aaa":"dddddddddd"}}
{% endhighlight %}

* 返回结果参数说明
	1. `status` (必须) 描述请求的状态

		| **值** | **意义** | **备注** |
		|:-------|:-------- |:---------|
		| success | 请求成功 | |
		| fail | 操作失败 | |
		| error | 应用错误信息 | 可能为数字状态，也可能为字符串提示信息，由具体的业务应用逻辑去协商处理 |
		| deny | 无权访问 | |
		| unlogin | 未登录/登录超时 | |
		| logined | 登录成功 | 
		{: rules="groups"}

	2. `data` (status为success时必须) 返回的json数据
	3. `secret` （非必须）返回数据是否需要解密 0：不需要（默认），1：需要