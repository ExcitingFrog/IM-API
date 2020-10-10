# Manager
>企业管理员接口

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:25px;font-size:15px;color:white" >POST</button> Sign Up </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/sign_up</b></pre>

注册管理员账号，传入邮箱，密码，账号名。 

既是网站账号密码 也是客服系统的账号密码。 

同时创建一个聊天室频道，名字是管理员id，作为管理客服的频道

<style>
td,th,tr {
 border-style : hidden!important;
 text-align:left;
 }
</style>
#### Request
<div>
<pre>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>name</th><td>string</td><td>姓名</td></tr>
    <tr><th>email</th><td>string</td><td>邮箱</td></tr>
    <tr><th>password</th><td>string</td><td>密码</td></tr>
    <tr><th>password_confirm</th><td>string</td><td>重复密码</td></tr>
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
      "channel": {
          "success": true,
          "error": "",
          "status": "",
          "message": "",
          "channel": {
              "_id": "iuCPJgmpfjQGZDNF9",
              "name": "f1098849-affa-4237-b358-6160e400c7f6",
              "t": "c",
              "usernames": null,
              "msgs": 0,
              "u": {
                  "_id": "i8X4tKM2NmWAKjDQj",
                  "username": "sh16"
              },
              "ts": "2020-09-17T03:19:53.325Z"
          }
      },
      "status": "register success"
  }
</pre>

<pre>
  失败:
  400 Bad Request
  Could not find a cake matching this query.
  返回:
  { "status": "password confirmation dismatch"}
</pre>

<pre>
  失败:
  409 Conflict
  Could not find a cake matching this query.
  返回:
  {"status": "account exists"}
</pre>

</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Sign In </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/sign_in</b></pre>

 管理员登录网页

#### Request
<div>
<pre>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>email</th><td>string</td><td>邮箱</td></tr>
    <tr><th>password</th><td>string</td><td>密码</td></tr>
  </table>
</pre>
</div>

#### Response
<div>
<pre>
  成功:
  200 OK
  token在返回头的Authorization 
  返回:
  {
    "manager_id": "f1098849-affa-4237-b358-6160e400c7f6",
    "status": "login success"
  }
</pre>

<pre>
  失败:
  401 Unauthorized
  返回:
  {"status": "account or password error"}
</pre>

<pre>
  失败:
  404 Not Found
  返回:
  {"status": "account not found"}
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Change Password </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/change_password</b></pre>

 修改个人密码

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>origin_password</th><td>string</td><td>old password</td></tr>
    <tr><th>password</th><td>string</td><td>new password</td></tr>
    <tr><th>password_confirm</th><td>string</td><td>new password confirmation</td></tr>
  </table>
</pre>
</div>

#### Response
<div>
<pre>
  成功:
  200 OK
  返回:
  {"status": "update password success"}
</pre>

<pre>
  失败:
  302 Found
  返回:
  {"status": "account or password error"}
</pre>

<pre>
  失败:
  400 Bad Request
  返回:
  {"status": "password confirmation dismatch"}
</pre>

<pre>
  失败:
  401 Unauthorized
  返回:
  {"status": "invalid"}
</pre>

</div>

---

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> Keys </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/keys</b></pre>

管理员获取apikey与secretKey 需要管理员登录时的token  

apikey就是管理员id  secretKey是随机生成的32位字符串（没有时间限制）重新请求会生成新的

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
</pre>
</div>

#### Response
<div>
<pre>
  成功:
  200 OK
  返回:
  {"api_key": apiKey, "secret_key": secretKey}
</pre>

<pre>
  失败:
  400 Bad Request
  返回:
  {"status": "invalid token"}
</pre>
</div>

---

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> Access token </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/access_token</b></pre>

通过apikey与appsecret获取token，这个token可以使用在customer的接口中 

签名生成方法(hmac sha256)样例： 

go: 

sha256 := sha256.New  

hash := hmac.New(sha256, []byte(secretKey)) 

hash.Write([]byte(apiKey)) 

return base64.StdEncoding.EncodeToString(hash.Sum(nil))

js: 

var hash = CryptoJS.HmacSHA256("8009bf1c5fea4221b19afd4278fcb06f",

 "3WsQAyIVHG7mQAHwURktAkLPMy622Has"); 

var hashInBase64 = CryptoJS.enc.Base64.stringify(hash); 

document.getElementById('output').innerHTML = hashInBase64;

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Form Data Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>apiKey</th><td>string</td><td>apikey 也就是manager_id</td></tr>
    <tr><th>signature</th><td>string</td><td>签名</td></tr>
  </table>
</pre>
</div>

#### Response
<div>
<pre>
  成功:
  200 OK
  返回token和过期时间   时间按照秒数来
  返回:
  {
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzY3AiOiJyb2NrZXQiLCJleHAiOjE2MDAyNjAwNzcsImp0aSI6ImQ4ZTVkNTYyLWFhMDQtNDU1OS04YTc3LTgwMThmMzZmY2FkZiIsImlhdCI6MTYwMDIxNjg3NywibmJmIjoxNjAwMjE2ODc3LCJzdWIiOiI2OWY0YzY2Ny0wZjEzLTRkMzQtODUzMC01YmY4ZDVhYjE0YjQifQ.vq_zSBVJczygilG9s6HJRDZ6LdyoBA_4WNVtvXZ7pwM",
    "time": 43200
  }
</pre>

<pre>
  失败:
  400 Bad Request
  apikey错误
  返回:
  {"status": "apiKey wrong"}
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Create Agent </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/access_token</b></pre>

管理员注册客服账号  

客服会加入大的管理员创建时的频道 和 其所在部门的部门频道

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
  Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>name</th><td>string</td><td>用户名</td></tr>
    <tr><th>password</th><td>string</td><td>密码</td></tr>
    <tr><th>email</th><td>string</td><td>邮箱</td></tr>
    <tr><th>depart_id</th><td>string</td><td>depart部门的uuid</td></tr>
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
    "status": "register success"
  }
</pre>

<pre>
  失败:
  401 Unauthorized
  返回:
  {"status":"unauthorized"}
</pre>
</div>

---

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> Query Agents </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/agents</b></pre>

查找所有客服

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
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
    "agents": [
        {
            "ID": "f1847b0b-a7ea-4693-9b36-4a677da5063c",
            "CreatedAt": "2020-09-17T12:44:32.655563+08:00",
            "UpdatedAt": "2020-09-17T12:44:32.655563+08:00",
            "manager_id": "f1098849-affa-4237-b358-6160e400c7f6",
            "nickname": "imte16",
            "email": "16@imte.com",
            "RcId": "sXRjyPErjocxamwyE",
            "RcName": "imte16plgKCp",
            "RcEmail": "Obh0KA16@imte.com",
            "EncryptedPassword": "$2a$10$C/LtYXP6LvGkfMgEMy.kIeL/CFz8OolmDHmMxUF95CmR2vn99ONQ.",
            "department": "a4d76c9a-7dc8-4ba6-9857-d8616e84f106"
        },
        {
            "ID": "add4693c-c28e-46e6-a855-e26518846a3b",
            "CreatedAt": "2020-09-17T13:07:42.470216+08:00",
            "UpdatedAt": "2020-09-17T13:17:07.597521+08:00",
            "manager_id": "f1098849-affa-4237-b358-6160e400c7f6",
            "nickname": "imte16.1",
            "email": "16.1@imte.com",
            "RcId": "zD3JyHfusAkg2wB64",
            "RcName": "imte16.1rLjLEO",
            "RcEmail": "xsTFya16.1@imte.com",
            "EncryptedPassword": "$2a$10$NekJNbB8Am3EY9ZV02bhqenOuKFkhsDrPrxdwsZvmVerOkRklTssm",
            "department": "a4d76c9a-7dc8-4ba6-9857-d8616e84f106"
        }
    ],
    "status": "success"
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> Show Departments </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/departments</b></pre>

 查看管理员创建的所有部门

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
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
    "departs": [
        {
            "ID": "a4d76c9a-7dc8-4ba6-9857-d8616e84f106",
            "CreatedAt": "2020-09-17T11:22:05.225824+08:00",
            "UpdatedAt": "2020-09-17T11:22:05.225824+08:00",
            "manager_id": "f1098849-affa-4237-b358-6160e400c7f6",
            "name": "部门1"
        },
        {
            "ID": "c935ba92-4227-4fec-8820-184e6e942777",
            "CreatedAt": "2020-09-17T12:42:26.077606+08:00",
            "UpdatedAt": "2020-09-17T12:42:26.077606+08:00",
            "manager_id": "f1098849-affa-4237-b358-6160e400c7f6",
            "name": "部门2"
        }
    ],
    "status": "success"
  }
  </pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Create Department </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/departments</b></pre>

 管理员创建部门  

同时会创建一个channel 名字是“${managerid}AND${departid}”

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>name</th><td>string</td><td>部门名字</td></tr>
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
    "depart": {
        "ID": "28c73280-1fea-4805-b06b-b358053f3443",
        "CreatedAt": "2020-09-17T14:18:03.024451309+08:00",
        "UpdatedAt": "2020-09-17T14:18:03.024451309+08:00",
        "manager_id": "f1098849-affa-4237-b358-6160e400c7f6",
        "name": "售后"
    },
    "status": "success"
	}
</pre>
</div>

---

###<div><button style="background-color: rgb(247, 125, 5);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >PUT</button> Update Department </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/departments</b></pre>

 更新部门名字  

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>name</th><td>string</td><td>更改后的名字</td></tr>
    <tr><th>depart_id</th><td>string</td><td>部门的uuid</td></tr>
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

###<div><button style="background-color: rgb(255, 70, 66);border:0px;width:70px;height:25px;border-radius:10px;font-size:15px;color:white" >DELETE</button> Delete Department </div>

<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/templates</b></pre>

删除模版.     

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>depart_id</th><td>string</td><td>部门的uuid</td></tr>
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
    "status": "success"
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Change Agent Password</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/agents/change_password</b></pre>

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Form Data Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>agent_id</th><td>string</td><td>agent id</td></tr>
    <tr><th>password</th><td>string</td><td>密码</td></tr>
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
    "status": "success"
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Change Agent Department</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/agents/change_department</b></pre>

 更改客服的部门  

客服会从所在的channel移到另一个channel

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>email</th><td>string</td><td>客服的邮箱</td></tr>
    <tr><th>depart_id</th><td>string</td><td>部门uuid</td></tr>
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
    "status": "success"
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Create Template</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/templates</b></pre>

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>manager_id</th><td>string</td><td>管理员的id</td></tr>
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
    "status": "success",
      "template": {
        "id": "5b62c499-6f20-4f53-9118-e7607a2bd198",
        "created_at": "2020-10-10T14:13:13.024172609+08:00",
        "updated_at": "2020-10-10T14:13:13.024172609+08:00",
        "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
        "department_id": "00000000-0000-0000-0000-000000000000",
        "text": "",
        "tag": ""
    }
  }
</pre>
</div>

---

###<div><button style="background-color: rgb(247, 125, 5);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >PUT</button> Update Template </div>

<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/templates</b></pre>

更新模版信息 

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>id</th><td>string</td><td>模版id</td></tr>
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
    "status": "success",
  }
</pre>
</div>

---

###<div><button style="background-color: rgb(255, 70, 66);border:0px;width:70px;height:25px;border-radius:10px;font-size:15px;color:white" >DELETE</button> Delete Template </div>

<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/departments</b></pre>

 删除部门 同时删除部门channel  

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
  </table>
Query Parameters
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>id</th><td>string</td><td>模版id</td></tr>
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

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> Query Template </div>

<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/templates</b></pre>

查询模版信息  

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>管理员登录获取的token</td></tr>
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
    "result": [
        {
            "id": "5b62c499-6f20-4f53-9118-e7607a2bd198",
            "created_at": "2020-10-10T14:13:13.024172+08:00",
            "updated_at": "2020-10-10T14:13:13.024172+08:00",
            "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
            "department_id": "00000000-0000-0000-0000-000000000000",
            "text": "text",
            "tag": "tag"
        },
        {
            "id": "8502ebe0-e235-45f0-ba64-1a5484735ca3",
            "created_at": "2020-10-10T14:13:38.679338+08:00",
            "updated_at": "2020-10-10T14:13:38.679338+08:00",
            "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
            "department_id": "00000000-0000-0000-0000-000000000000",
            "text": "text",
            "tag": ""
        },
        {
            "id": "525588ec-4273-4c41-aa2b-edc30ff4d1b3",
            "created_at": "2020-10-10T14:13:46.708349+08:00",
            "updated_at": "2020-10-10T14:13:46.708349+08:00",
            "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
            "department_id": "00000000-0000-0000-0000-000000000000",
            "text": "",
            "tag": ""
        },
        {
            "id": "c927c112-ace3-4f9e-a641-4d62da539541",
            "created_at": "2020-10-10T14:22:32.877917+08:00",
            "updated_at": "2020-10-10T14:22:43.802195+08:00",
            "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
            "department_id": "00000000-0000-0000-0000-000000000000",
            "text": "",
            "tag": ""
        }
    ],
    "status": "success"
  }
</pre>
</div>

---

### 

