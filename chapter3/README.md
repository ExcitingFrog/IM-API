# Agent
>客服接口

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Sign In </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>agents/sign_in</b></pre>

 sign in

#### Request
<div>
<pre>
Form Data Parameters
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
  {
    "agent": {
        "id": "bfe28993-1023-4322-8cc7-1419e1524164",
        "created_at": "2020-09-22T09:02:26.313433+08:00",
        "updated_at": "2020-09-22T09:02:26.313433+08:00",
        "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
        "nickname": "a2",
        "email": "a2@ruilisi.co",
        "rc_id": "gMMDnqdZmHpeAjGXb",
        "rc_name": "a2xpFbOg",
        "rc_email": "YqfPdJa2@ruilisi.co",
        "EncryptedPassword": "$2a$10$iwptFOgJc3YgjZvTzeGfjO7MlBStVepXl8Gymxoa.tOXiAQkLG1km",
        "departments": [
            "0a17b060-f6ed-43e1-a55f-5c4a6ec1e16b"
        ]
    },
    "status": "success"
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Change Password </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>agents/change_password</b></pre>

#### Request
<div>
<pre>
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

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> History Message</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>agents/history_message</b></pre>

---

###<div> <button style="background-color: rgb(56, 132, 255);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >GET</button> Query Template </div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>agents/templates</b></pre>

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>agent登录获取的token</td></tr>
  </table>
Query Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>tag</th><td>string</td><td>template tag</td></tr>
    <tr><th>department_id</th><td>string</td><td>template id</td></tr>
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
        }
    ],
    "status": "success"
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Create Template</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>agents/templates</b></pre>

#### Request
<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>agent登录获取的token</td></tr>
  </table>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>manager_id</th><td>string</td><td>manager id</td></tr>
    <tr><th>tag</th><td>string</td><td>template tag</td></tr>
    <tr><th>department_id</th><td>string</td><td>template id</td></tr>
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
        "id": "28310ee9-d0df-4b3c-b570-07fe248963eb",
        "created_at": "2020-10-10T15:31:48.581911397+08:00",
        "updated_at": "2020-10-10T15:31:48.581911397+08:00",
        "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
        "department_id": "00000000-0000-0000-0000-000000000000",
        "text": "",
        "tag": ""
    }
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Post Message</div>

#### Request

<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>agent登录获取的token</td></tr>
  </table>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>roomId</th><td>string</td><td>group id</td></tr>
    <tr><th>text</th><td>string</td><td>message</td></tr>
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
    "msg": {
        "success": true,
        "error": "",
        "status": "",
        "message": {
            "_id": "EzvWbriNb6JTCET3B",
            "rid": "2npDFBKwJLuPYen3F",
            "msg": "msg",
            "ts": "2020-10-10T08:02:04.949Z",
            "_updatedAt": "2020-10-10T08:02:05.019Z",
            "u": {
                "_id": "gMMDnqdZmHpeAjGXb",
                "name": "a2",
                "username": "a2xpFbOg",
                "status": "",
                "token": "",
                "tokenExpires": 0
            },
            "parseUrls": true
        }
    },
    "status": "success"
  }
</pre>
</div>

---

###<div> <button style="background-color: rgb(38, 203, 124);border:0px;width:60px;height:25px;border-radius:10px;font-size:15px;color:white" >POST</button> Send Template</div>

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>agents/send_template</b></pre>

#### Request

<div>
<pre>
Headers
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>Authorization</th><td>string</td><td>agent登录获取的token</td></tr>
  </table>
Form Data Parameters 
  <table>
    <tr><th>参数</th><th>类型</th><th>说明</th></tr>
    <tr><th>template_id</th><td>string</td><td>template id</td></tr>
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
        "id": "28310ee9-d0df-4b3c-b570-07fe248963eb",
        "created_at": "2020-10-10T15:31:48.581911+08:00",
        "updated_at": "2020-10-10T15:31:48.581911+08:00",
        "manager_id": "8427ed6a-0376-4272-9039-b71600ebb99c",
        "department_id": "00000000-0000-0000-0000-000000000000",
        "text": "",
        "tag": ""
    }
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

