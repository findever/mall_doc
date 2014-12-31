---
layout: post
title: json数据模拟
category: app_api
author: "findever"
---

## 本地用于模拟json数据api接口

<!--more-->

### api介绍

  该api用php语言编写，将所有`GET`请求的`url`链接（ex:`http://mall.com/a/b?id=3`)按照规则转换，并在项目根目录下的`test`文件夹（`/test`）中对应目录下生成json文件，此文件路径为`__ROOT__/test/url_path/url_query.json`(ex:`/test/a/b/id=3.json`)。
  
### 功能演示

- `url`中有`url_query`

~~~javascript
//GET http://mall.com/a/b?name=lisi&age=99
http://mall.com/api.php?_p=a/b&name=lisi&age=99&_debug
//JSON_FILE_PATH => __ROOT__/test/a/b/name=lisi&age=99.json
//api会在项目的 test/a/b/ 目录下生成文件名为 name=lisi&age=99 的json文件
~~~
- - -
  
  
- `url`中无`url_query`

~~~javascript
//GET http://mall.com/a/b
http://mall.com/api.php?_p=a/b&_debug
//JSON_FILE_PATH => __ROOT__/test/a/b/index.json
//api会在项目的 test/a/b/ 目录下生成文件名为 index 的json文件(index为默认json文件名）
~~~
- - -
  
  
- server_config配置

  文件路径：`__ROOT__/api/server_config.php`, api将按照给定的配置对json文件重命名, 不配置则按照上述演示生成json文件名
  
~~~php
server_config 初始配置如下：
<?php
	// 请求path => array(正则 => 实际文件名·无后缀)
	return array(
		"url_path" => array(
				"/req/i" => "new_file_name"
					)
	);
?>

//如对其配置如下：
<?php
	// 请求path => array(正则 => 实际文件名·无后缀)
	return array(
		"a/b" => array(
				"/id=1/i" => "id1",
				"/id=2/i" => "id2"
					)
	);
?>

//api将根据上述正则, 对url进行匹配转换

//GET http://mall.com/a/b?id=1
http://mall.com/api.php?_p=a/b&id1&_debug
//JSON_FILE_PATH => __ROOT__/test/a/b/id1.json
//api会在项目的 test/a/b/ 目录下生成文件名为 id1 的json文件

//GET http://mall.com/a/b?id=2
http://mall.com/api.php?_p=a/b&id2&_debug
//JSON_FILE_PATH => __ROOT__/test/a/b/id2.json
//api会在项目的 test/a/b/ 目录下生成文件名为 id2 的json文件

~~~

- json文件覆盖规则

~~~php
//GET http://mall.com/a/b?name=lisi
http://mall.com/api.php?_p=a/b&name=lisi&_debug
若存在`__ROOT__/test/a/b/name=lisi.json`, api将不会在`__ROOT__/test/a/b`下创建json文件。
~~~
