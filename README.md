
# 运行项目

```bash
// 克隆项目
git clone https://github.com/sunniejs/vue-wechat-auth.git

// 进入目录
cd vue-wechat-auth

// 安装依赖
npm install  

// 运行项目
npm run serve

```

## 实现本地微信授权

1.工具
实现本地开发授权，你需要使用微信开发者工具，网页是没有办法直接本地拿到授权的。

2.将auth.html部署到服务器上
为什么要部署auth.html呢？

实现微信授权，微信官方要你填写一个授权回到页面域名，授权的地址必须是这个域名:

 (1) 前往微信公众平台->接口权限->网页授权获取用户基本信息->修改，填写授权回调页面域名，例如www.shouquan.com

 (2)微信要求将MP_verify_xxx.txt文件放到服务器下。按照提示操作。

 (3) 部署auth.html(在github项目的根目录下) ，相同的，将 auth.html 上传至填写域名或路径指向的web服务器（或虚拟主机）的目录

 （ 例如 ：http://www.shouquan.com/auth.html），不一定是根目录(https://www.shouquan.com/xxx/auth.html   ),并确保可以访问。

### 碰到问题

  1、携带的参数在授权完之后没能全部带回来。

  2、hash回调url错误问题

  有兴趣的朋友可以去了解，非常感谢作者  https://github.com/HADB/GetWeixinCode

#### 设置变量  

  在开发之前你要首先在下面三个文件设置两个变量，如果你已经启动项目，设置后需要重启。
  
  .env.development .env.staging .env.production
  
  VUE_APP_WECHAT_APPID  是你的appid

  VUE_APP_WECHAT_AUTH_URL ="http://www.shouquan.com/auth.html"  你的访问地址

##### 授权相关方法

  文件路径：src/plugins/wechatAuth.js，主要是先微信跳转地址拼接，获取地址参数等

###### 路由守卫

  src/permission.js 里实现了主要的逻辑。
