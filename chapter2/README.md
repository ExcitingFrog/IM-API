# Manager
>企业管理员接口

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Sign Up

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/sign_up</b></pre>

注册管理员账号，传入邮箱，密码，账号名。 

既是网站账号密码 也是客服系统的账号密码。 

同时创建一个聊天室频道，名字是管理员id，作为管理客服的频道。

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Sign In

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/sign_in</b></pre>

 管理员登录网页

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Change Password

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/change_password</b></pre>

 修改个人密码

---

### <button style="background-color: rgb(56, 132, 255);width:80px;height:30px;border-radius:7px;font-size:17px;color:white" >GET</button> Keys

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/keys</b></pre>

管理员获取apikey与secretKey 需要管理员登录时的token  

apikey就是管理员id  secretKey是随机生成的32位字符串（没有时间限制）重新请求会生成新的

---

### <button style="background-color: rgb(56, 132, 255);width:80px;height:30px;border-radius:7px;font-size:17px;color:white" >GET</button> Access token

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

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Create Agent

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/access_token</b></pre>

管理员注册客服账号  

客服会加入大的管理员创建时的频道 和 其所在部门的部门频道

---

### <button style="background-color: rgb(56, 132, 255);width:80px;height:30px;border-radius:7px;font-size:17px;color:white" >GET</button> Query Agents

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/agents</b></pre>

查找所有客服

---

### <button style="background-color: rgb(56, 132, 255);width:80px;height:30px;border-radius:7px;font-size:17px;color:white" >GET</button> Show Departments

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/departments</b></pre>

 查看管理员创建的所有部门

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Create Department

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/departments</b></pre>

 管理员创建部门  

同时会创建一个channel 名字是“${managerid}AND${departid}”

---

### <button style="background-color: rgb(247, 125, 5);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >PUT</button> Update Department

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>/managers/departments</b></pre>

 更新部门名字  

---

### <button style="background-color: rgb(255, 70, 66);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >DELETE</button> Delete Department

<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/templates</b></pre>

删除模版.     

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Change Agent Password

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/agents/change_password</b></pre>

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Change Agent Department

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/agents/change_department</b></pre>

 更改客服的部门  

客服会从所在的channel移到另一个channel

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Create Template

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>managers/templates</b></pre>

---

### <button style="background-color: rgb(247, 125, 5);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >PUT</button> Update Template
<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/templates</b></pre>

更新模版信息 

---

### <button style="background-color: rgb(255, 70, 66);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >DELETE</button> Delete Template
<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/departments</b></pre>

 删除部门 同时删除部门channel  

---

### <button style="background-color: rgb(56, 132, 255);width:80px;height:30px;border-radius:7px;font-size:17px;color:white" >GET</button> Query Template

<pre><span style="color:grey">https://api.chatsdk.io/departments/</span><b>managers/templates</b></pre>

查询模版信息  

---

### 
