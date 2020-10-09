# 接口总览
>这里显示所有的接口

## 测试 

|  API   | FUNCTION  |
|  :----  | :----  |
| [Ping](https://app.gitbook.com/@cs-server/s/cs-server/)  | 测试连通性 |

---

## Manager
|  API   | FUNCTION  |
|  :----  | :----  |
| [Sign Up](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHiOuojS4Pc2DKdCYSZ/amdin#sign-up)  | 注册管理员账号 |
| [Sign In](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#sign-in)  | 管理员登录 |
| [Create Department](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#creare-department)  | 管理员创建客服部门 |
| [Delete Department](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#delete-department)  | 管理员删除客服部门 |
| [Update Department](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#update-department)  | 管理员更新部门信息 |
| [List Department](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#show-departments)  | 管理员查看所有部门信息 |
| [Create Agent](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#create-agent)  | 管理员创建客服 |
| [Delete Agent](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#delete-agent)  | 管理员删除客服 |
| [Create Template](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#create-template)  | 管理员创建模版信息 |
| [Delete Template](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#delete-template)  | 管理员删除模版信息 |
| [Update Template](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#update-template)  | 管理员更新模版信息 |
| [Query Template](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#query-template)  | 管理员查询模版信息 |
| [Keys](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#keys)  | 管理员获取apikey和secretkey |
| [Access Token](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#access-token)  | 获取accesstoken用于customer接口 |
| [Change Password](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#change-password)  | 修改管理员密码 |

---

## Agent 

|  API   | FUNCTION  |
|  :----  | :----  |
| [Sign In](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHiOuojS4Pc2DKdCYSZ/agent)  | 客服登录 |
| [Change Password](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/agent)  | 客服修改密码 |
| [History Message](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/agent#history-messages)  | 客服查看历史消息 |
| [Query Template](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/agent#query-template)  | 客服查询模版 |
| [Create Template](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/agent#create-template)  | 客服创建模版 |
| [Post Message](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/agent#post-message)  | 客服发送消息 |
| [Send Template](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/amdin#delete-template)  | 客服返送模版信息 |

---

## Customer

|  API   | FUNCTION  |
|  :----  | :----  |
| [Connect](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHiOuojS4Pc2DKdCYSZ/user#connect)  | 需要apikey和signature的用户创建客服聊天 |
| [Transfer](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/user#transfer)  | 转接 |
| [ShutDown Service](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/user#shutdown-service)  | 用户问题处理完成，关闭客服服务 |
| [History Messages](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/user#history-messages)  | 用户查询历史消息 |
| [ClientConnect](https://app.gitbook.com/@cs-server/s/cs-server/~/drafts/-MHoaYVbY1aoByxkhIwl/user#client-connect)  | 只需要apikey的用户创建客服聊天 |


