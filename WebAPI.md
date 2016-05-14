# “闪开”API接口说明

[toc]

#### 1：小区注册

 使用之前必须先注册小区信息，获得小区的ID

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/create_organization?access_token=ACCESS_TOKEN
		POST数据格式：json
		POST数据例子：{"name":"桃花园小区","address":"地址","contact":"0755-1234567","ic_id_mode":"1"}


* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|name|	必填	|名称|
	|address|	可选|	详细地址|
	|contact|	可选	|联系方式|
	|ic_id_mode|	必填	|ic卡/ID卡模式    0为ID卡 1为IC卡|
* #####返回说明
		{
			"errcode":0,
			"errmsg":"ok",
			"data":{
				"org_id":"oDF3iY9ffA-hqb2vVvbr7qxf6A0Q"
			}

		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确，10001，表示小区已注册|
	|errmsg|错误信息, ok表示正确	|
	|org_id|小区ID	|	

#### 2：得到小区ID

 根据小区的名称，获得小区的ID

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/get_organization?access_token=ACCESS_TOKEN
		POST数据格式：json 
		POST数据例子：{"name":"桃花园小区"}



* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|name|	可选	|名称|
* #####返回说明
		{ 
			"errcode":0,
			"errmsg":"ok",
			"data":{
				"org_id":"oDF3iY9ffA-hqb2vVvbr7qxf6A0Q"
			}

		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确|
	|errmsg|错误信息, ok表示正确	|
	|org_id|小区ID	|
#### 3：更新小区信息

 更新小区信息

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/update_organization?access_token=ACCESS_TOKEN
		POST数据格式：json
		POST数据例子：{"org_id":"oDF3iY9ffA-hqb2vVvbr7qxf6A0Q","name":"桃花园小区",”city“:"深圳","district":"宝安区","address":"地址","contact":"0755-1234567","ic_id_mode":"1"}


* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|name|	必填	|名称|
	|org_id|	必填	|小区ID|    
	|city|	可选|	所在城市|
	|district|	可选	|所在区|
	|address|	可选|	详细地址|
	|contact|	可选	|联系方式|
	|ic_id_mode|	必填	|ic卡/ID卡模式    0为ID卡 1为IC卡|
* #####返回说明
		{
			"errcode":0,
			"errmsg":"ok",
		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确|
	|errmsg|错误信息, ok表示正确	|
	|org_id|小区ID	|	
    
#### 4：删除小区

 删除小区信息

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/del_organization?access_token=ACCESS_TOKEN
		POST数据格式：json
		POST数据例子：{"org_id":"oDF3iY9ffA-hqb2vVvbr7qxf6A0Q"}


* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|org_id|	必填	|小区ID|    
* #####返回说明
		{
			"errcode":0,
			"errmsg":"ok",
		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确|
	|errmsg|错误信息, ok表示正确	|
	|org_id|小区ID	|
    
#### 5：给用户写卡

 根据用户手机号设置卡号,只适用用IC卡模式

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/set_card_no?access_token=ACCESS_TOKEN
		POST数据格式：json 
		POST数据例子:{"org_id":"oDF3iY9ffAhqb2vVvbr7qxf6A0Q",
		"mobile":"13823781234","name":"张三",”card_no”:123456}



* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|org_id|必填	|小区ID|
	|mobile|必填|用户手机号|
	|name|必填|用户姓名|
	|card_no|必填|卡号，支持10进制和16进制两种输入<br>1. 输入数字为10进制格式，最大不能超过2147483647 <br>2. 输入0x开头，表示16进制数据，最大不能超过22个字节, <br>例如:0x1A3D5B79|
* #####返回说明
		{
			"errcode":0,
			"errmsg":"ok",
		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确|
	|errmsg|错误信息, ok表示正确|
#### 6：读取用户卡号

 根据用户手机号，获得该用户的卡号，如果没有设置，系统会分配一个

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/get_card_no?access_token=ACCESS_TOKEN
		POST数据格式：json 
		POST数据例子:{"org_id":"oDF3iY9ffA-hqb2vVvbr7qxf6A0Q","mobile":"13823781234","name",""}



* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|org_id|必填	|小区ID|
	|mobile|必填|用户手机号|
	|name|可选|用户姓名，ID卡模式下，如果用户不存在，会增加一个用户|    
	
* #####返回说明
		{ 
			"errcode":0,
			"errmsg":"ok",
			"data":{"card_no":123456,"is_new":"true"}
		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确|
	|errmsg|错误信息, ok表示正确|	
	|card_no|卡号 （16进制）|	
	|is_new|是否系统新生成卡号|	

#### 7：删除用户卡号

 删除用户卡，回收卡

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/del_user?access_token=ACCESS_TOKEN
		POST数据格式：json 
		POST数据例子：{"org_id":"oDF3iY9ffA-hqb2vVvbr7qxf6A0Q","mobile":"13823781234"}


* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|org_id|必填	|小区ID|
	|mobile|必填|用户手机号|

* #####返回说明
		{
			"errcode":0,
			"errmsg":"ok"
		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确|
	|errmsg|错误信息, ok表示正确|

#### 8：设置小区管理处Web用户
	给小区增加一个初始用户

* #####接口调用请求说明

		http请求方式: POST（请使用https协议）
		https://api.baohe.tv:8081/1.0/set_admin_user?access_token=ACCESS_TOKEN
		POST数据格式：json
		POST数据例子：{"org_id":"oDF3iY9ffA-hqb2vVvbr7qxf6A0Q","login":"","pass":""}

* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|access_token|	必填	|调用接口凭证|
	|org_id|必填	|小区ID|
	|login|必填|登陆帐号|
    |pass|必填|登陆密码|

* #####返回说明
		{
			"errcode":0,
			"errmsg":"ok"
		}
	|参数|说明|
	|:---:|:---:|
	|errcode|错误码返回 0表示正确|
	|errmsg|错误信息, ok表示正确|


#### 附1：获取access token

* #####接口调用请求说明

		http请求方式: GET（请使用https协议）
		https://api.baohe.tv:8081/1.0/get_access_token?app_id=APPID&secret=APPSECRET

* #####参数说明
	|参数|是否必须|说明|
	|:---:|:---:|:---:|
	|app_id|必须|开发者ID	|
	|secret|必须|开发者密码|

* #####返回说明
		{
			"errcode":0,
			"errmsg":"ok",
 			"data":{
				"access_token":"ACCESS_TOKEN",
				"expires_in":7200
			}
		}
	|参数|说明|
	|:---:|:---:|
	|expires_in|凭证有效时间，单位：秒	|

#### 附2：全局返回码

* #####全局返回码

	|返回值|说明|
	|:---:|:---:|
	|0|请求成功	|
	|-1|系统异常|
	|1001|单位已注册|
	|4001|appid不存在或secret密码不正确|
	|4002|access_token已经过期|
	|4004|手机号找不到对应的用户|
	|4005|单位不存在|
    |4006|卡号输入不正确，<br>直接输入数字为10进制格式，最大不能超过2147483647，<br>输入0x开头，表示16进制数据，最大不能超过22个字节, <br>例如:0x1A3D5B79|
	|4007|ID卡模式不能设置卡号|
	|4008|帐号已存在|
	|4009|该门禁已添加|
	|4010|该门不存在|
	|4011|该用户在本小区没有开通权限|    



