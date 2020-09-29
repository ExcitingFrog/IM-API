# Customer
>IM接口，需要使用manager通过apikey和secretkey生成的token。这些接口提供给企业内的用户去与企业的客服进行交互。

---

### <button style="background-color: rgb(56, 132, 255);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >GET</button> Auth ping

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/auth_ping</b></pre>

verify access_token

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Connect

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/connect</b></pre>

 使用后 创建一个客服系统下的客户账号 连接企业客服 优先随机选择一个在线客服连接  

---

### <button style="background-color: rgb(56, 132, 255);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >GET</button> History Messages

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/history_message</b></pre>

 客户查看客服聊天的历史记录



---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> ShutDown Service

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/shutdown_service</b></pre>

 问题解决后 客户选择关闭会话（注意不会保留历史记录）

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Transfer

<pre><span style="color:grey">https://api.chatsdk.io/</span><b>customers/Transfer</b></pre>

转接客服

---

### <button style="background-color: rgb(38, 203, 124);width:80px;height:30px;border-radius:7px;font-size:15px;color:white" >POST</button> Client Connect

