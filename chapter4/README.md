# Customer
>IM接口，需要使用manager通过apikey和secretkey生成的token。这些接口提供给企业内的用户去与企业的客服进行交互。

---

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> Auth ping </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/auth_ping</b></pre>

verify access_token

#### Request

<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>access_token from admin api</td></tr>
  </table>
</pre>
</div>

#### Response

<div>
<pre>
  成功:
  200 OK
  返回:
  "pong"
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Connect</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/connect</b></pre>

 使用后 创建一个客服系统下的客户账号 连接企业客服 优先随机选择一个在线客服连接  

#### Request

<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>access_token from admin api</td></tr>
  </table>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>name</th><td>string</td><td>名字加管理员id作为客户账号 密码默认HelloWorld1@#</td></tr>
  </table>
</pre>
</div>

#### Response

<div>
<pre>
  成功:
  200 OK
  rid是房间号  
  username是账户名  
  token是客服系统的token   
  返回:
  {
    "base": "https://chat.esheeps.com",
    "config": {},
    "im": {
        "_id": "XetrKGqEZcNzxTRW8",
        "type": "user",
        "status": "offline",
        "active": true,
        "name": "suzhouxiaofangshuan",
        "utcOffset": 0,
        "username": "suzhouxiaofangshuan8009bf1c-5fea-4221-b19a-fd4278fcb06f"
    },
    "rid": "JR945hGSmuAuY6NnmXetrKGqEZcNzxTRW8",
    "token": "qoCA9uHhlkGrSBBXtiTIZAVIGQ2OaMNJ1zlYAQVlsRl"
  }
</pre>

<pre>
  失败:
  400 Bad Request
  数据传输错误
  返回:
  {"status": "params invalid"}
</pre>

<pre>
  失败:
  401 Unauthorized
  token错误
  返回:
  {"status": "unauthorized"}
</pre>
</div>

---

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> History Messages </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/history_message</b></pre>

 客户查看客服聊天的历史记录

#### Request

<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>token</td></tr>
  </table>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>room_id</th><td>string</td><td>group id</td></tr>
  </table>
</pre>
</div>

#### Response

<div>
<pre>
  成功:
  200 OK
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> ShutDown Service</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/shutdown_service</b></pre>

 问题解决后 客户选择关闭会话（注意不会保留历史记录）

#### Request

<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>token</td></tr>
  </table>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>group_id</th><td>string</td><td>group id</td></tr>
  </table>
</pre>
</div>

#### Response

<div>
<pre>
  成功:
  200 OK
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Transfer</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/Transfer</b></pre>

转接客服

#### Request

<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>token</td></tr>
  </table>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>agent_id</th><td>string</td><td>agent id</td></tr>
    <tr><th>group_id</th><td>string</td><td>group id</td></tr>
    <tr><th>department_id</th><td>string</td><td>department id</td></tr>
  </table>
</pre>
</div>

#### Response

<div>
<pre>
  成功:
  200 OK
  返回:
  {
    "agent_id": "YxpjNEmJzP2KqphR3",
    "base": "https://chat.esheeps.com",
    "config": {},
    "customer_name": "u1.1.1.1.1",
    "group_name": "depart2_u1.1.1.1.1_d2646257-3107-4441-81fd-305101a3bc2e",
    "id": "6FozWugWH3ybRJACx",
    "rid": "2npDFBKwJLuPYen3F",
    "status": "success",
    "template": "",
    "timeout": 200,
    "token": "3EDgHbTlrUN4AHDyrSvhIl2-XM0Vg-n6h9zZ34yDWPo",
    "user_id": "9e7eb98f-7f22-40a6-8068-adc4a3b6fef6",
    "wait": 0
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Client Connect</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/client_connect</b></pre>

客户连接

#### Request

<div>
<pre>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>api_key</th><td>string</td><td>api_key</td></tr>
    <tr><th>group_id</th><td>string</td><td>group id</td></tr>
    <tr><th>department_id</th><td>string</td><td>department id</td></tr>
  </table>
</pre>
</div>

#### Response

<div>
<pre>
  成功:
  200 OK
  返回:
  {
    "agent_id": "gMMDnqdZmHpeAjGXb",
    "base": "https://chat.esheeps.com",
    "config": {},
    "customer_name": "u1.1.1.1.2",
    "group_name": "depart1_u1.1.1.1.2_0a17b060-f6ed-43e1-a55f-5c4a6ec1e16b",
    "id": "N27A8jFtniXt5qngz",
    "rid": "GrnBZAv7r2yixD7Wh",
    "status": "success",
    "template": "",
    "timeout": 200,
    "token": "KQkPB3YqsKA6toH4mpH-L1QsZmSbTdqrTKU27-gBE3Q",
    "user_id": "62908c52-036f-4a98-967e-dd08fde88050",
    "wait": 0
  }
</pre>
</div>

---

<style>
td,th,tr {
 border-style : hidden!important;
 text-align:left;
 }
</style>

