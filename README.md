# Introduction
IM使用说明

# 接口分类 
- manager接口是企业管理员的接口，通过管理员登录获取的token来调用，这一部分负责管理企业内的客服，模板以及部门等内容
- agent接口是客服的接口，主要负责客服的沟通，创建模板等基本功能
- customer接口是客户端的接口，通过appkey和secretkey获取的token来进行调用

# 使用步骤 
1. 注册管理员账号 
2. 登录后创建部门
3. 创建客服账号
4. 管理页面获取api key和 token
5. 获取access_token，凭此token（12小时过期 可提前请求更新）可以使用customer接口


