## 两个Heroku仓库被封，不玩了。捐赠地址（TRC20）：TScd7U9QUXZVS6DawwoRPHnNminreN4fJp

## 注意事项
1）5月8日晚，CloudFlare Workers 的业务域名 Workers.dev 被防火长城 DNS 污染、SNI阻断。

2）CloudFlare Workers，可自定义workers域名，教程已更新至博客`ifts.ml`；经过添加自定义域名，更换Host和SNI后已可正常使用。

#### 交流群[https://t.me/iflugp](https://t.me/iflugp)

### 提示：UUID请使用UUID生成器，推荐[UUID Generator](https://www.uuidgenerator.net/)

### 提醒：滥用可能导致账户被删除！！！

### 提醒：配置连接方式时请仔细阅读带粗体的注意事项! ! !

### 请之前已经fork过的用户删除项目后重新fork本项目! ! !

### 已恢复Vmess、VLESS、Trojan、Shadowsocks的所有连接! ! !

### 想改其他传输协议的请参考[HTTP路由/HTTP支持版本](https://devcenter.heroku.com/articles/http-routing#http-versions-supported)然后酌情修改，仅限有经验用户修改，因修改传输协议出现连接错误的本项目不承担任何责任！！！

## 服务端创建操作流程

0.给本项目个stars

1.将本项目fork至自己仓库修改`Deploy to Heroku`按键指向地址为自己仓库地址

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/DaoChen6/IF-XTW) 

2.点击上面紫色`Deploy to Heroku`，会跳转到heroku app创建页面，应用程序名无需填写也能创建，名字会由heroku随机生成，选择节点（美国或者欧洲），新用户只需要自定义UUID码和CADDYIndexPage（参考：[Caddy主页配置](https://github.com/DaoChen6/IF-XTW/blob/master/README.md#5caddy%E4%B8%BB%E9%A1%B5%E9%85%8D%E7%BD%AE))，其他建议保持默认，点击下面deploy，几秒后搞定！   

3.若出现`We couldn't deploy your app because the source code violates the Salesforce Acceptable Use and External-Facing Services Policy.`提示，则返回仓库，>`Setting`>`Repository name`修改仓库名。

4.若执行了第3步修改仓库名的操作，则必须修改app.json中的name和description，十分重要，切记！！！！

5.注意`repository`必须留空以免项目被禁

6.再修改`Deploy to Heroku`按键指向地址为自己仓库地址，重复`2`的操作

7.带有删除线的部分表示已经废弃或不适用

## vmess vless trojan-go shadowsocks对应客户端参数的参考如下,末尾带()里的内容仅为提示

## 1：Xray Vmess/VLESS ws+tls

|**属性**|**对应值**|
|:------:|:---------:|
|**代理协议**|VLESS+ws+tls</br>Vmess+ws+tls|
|服务器地址|自选ip（如：`uicdn.cf`或`icook.tw`）</br>应用程序名.herokuapp.com|
|端口|443|
|默认UUID|8f91b6a0-e8ee-11ea-adc1-0242ac120002</br>**注意：务必创建时自定义UUID码**|
|加密|Vmess: Auto</br>VLESS: none</br>**注意：Vmess默认禁止以下加密方式连接：none、aes-128-cfb**|
|传输协议|ws|
|伪装类型|none|
|伪装host|xxxx.workers.dev(CF Workers反代地址)</br>应用程序名.herokuapp.com|
|SNI地址|xxxx.workers.dev(CF Workers反代地址)</br>应用程序名.herokuapp.com|
|Path路径|/自定义UUID码-vless</br>/自定义UUID码-vmess</br>**注意：前有斜杠/** |
|Vmess额外id（alterid）|0</br>默认启用AEAD</br>**注意：此选项将于2022.1.1之后废弃不用，请使用者及时更新最新的客户端以解决此问题。仅对使用Xray-core的用户有影响。**|
|底层传输安全|tls|
|跳过证书验证|false|

## 2：Xray Trojan ws+tls

|**属性**|**对应值**|
|:------:|:-------:|
|服务器地址|自选ip（如：`uicdn.cf`或`icook.tw`）</br>应用程序名.herokuapp.com|
|端口|443|
|密码|8f91b6a0-e8ee-11ea-adc1-0242ac120002</br>**注意：务必创建时自定义UUID码**|
|传输协议|ws|
|Path路径|/自定义UUID码-trojan</br>**注意：前有斜杠/**|
|SNI地址|xxxx.workers.dev(CF Workers反代地址)</br>应用程序名.herokuapp.com|
|伪装host</br>TLS Host|xxxx.workers.dev(CF Workers反代地址)</br>应用程序名.herokuapp.com|

## 3：Xray Shadowsocks ws+tls

|**属性**|**对应值**|
|:------:|:-------:|
|服务器地址|自选ip（如：`uicdn.cf`或`icook.tw`）</br>应用程序名.herokuapp.com|
|端口|443|
|密码|8f91b6a0-e8ee-11ea-adc1-0242ac120002</br>**注意：务必创建时自定义UUID码**|
|加密方式|chacha20-ietf-poly1305</br>[调整加密方式请参考](https://www.v2fly.org/config/protocols/shadowsocks.html#%E5%8A%A0%E5%AF%86%E6%96%B9%E5%BC%8F%E5%88%97%E8%A1%A8)|
|传输协议|ws|
|伪装类型|none|
|ivCheck|true|
|伪装host</br>TLS Host|xxxx.workers.dev(CF Workers反代地址)</br>应用程序名.herokuapp.com|
|Path路径|/自定义UUID码-ss</br>**注意：前有斜杠/**|
|**注意事项**|**1.加密方式选项仅限有经验的用户调整，因调整错误所发生的后果本项目不承担任何责任！**</br>**2.使用lean lede的SSRPlus+/Passwall的用户现可使用Xray/v2ray Shadowsocks ws+tls连接。**|

## 4：Trojan+ws+tls客户端支持状态（不定期更新）

|客户端|是否支持Trojan+ws+tls|
|:----:|:------------------:|
|2dust V2RayN</br>2dust V2RayNG|是，需要V2RayN4.26+或V2RayNG最新版本(Pre-release)</br>需要电脑端.net framework 6.0及更高版本|
|OpenWrt SSRPlus+|是|
|OpenWrt Passwall|是，需要最新版本passwall|
|~~QV2Ray~~|~~QV2Ray~~|

## 5：Caddy主页配置

# Caddyindexpage变量 (欢迎大佬Pull Requests)

* 从以下链接中复制喜欢的主页链接到CADDYIndexPage变量中

|#|地址|
|:-:|:-:|
| 1(默认) | [欢迎使用caddy页面](https://raw.githubusercontent.com/caddyserver/dist/master/welcome/index.html) |
| 2 | [3DCEList元素周期表](https://github.com/wulabing/3DCEList/archive/master.zip) |
| 3 | [Spotify-Landing-Page-Redesign](https://github.com/WebDevSimplified/Spotify-Landing-Page-Redesign/archive/master.zip) |
| 4 | [dev-landing-page](https://github.com/flexdinesh/dev-landing-page/archive/master.zip) |
| 5 | [free-for-dev](https://github.com/ripienaar/free-for-dev/archive/master.zip) |
| 6 | [tailwindtoolbox-Landing-Page](https://github.com/tailwindtoolbox/Landing-Page/archive/master.zip) |
| 7 | [sandhikagalih/simple-landing-page](https://github.com/sandhikagalih/simple-landing-page/archive/master.zip) |
| 8 | [StartBootstrap/startbootstrap-new-age](https://github.com/StartBootstrap/startbootstrap-new-age/archive/master.zip) |
| 9 | [mikutap 一个好玩带音乐的页面](https://github.com/AYJCSGM/mikutap/archive/master.zip)<br>[演示](https://aidn.jp/mikutap) |
| 10 | [WebGL流体模拟](https://github.com/PavelDoGreat/WebGL-Fluid-Simulation/archive/master.zip)<br>[演示](https://paveldogreat.github.io/WebGL-Fluid-Simulation/) |
| 11 | [loruki-website](https://github.com/bradtraversy/loruki-website/archive/master.zip) |
| 12 | [bongo.cat一只音乐的猫](https://github.com/Externalizable/bongo.cat/archive/master.zip)<br>[演示](https://bongo.cat/) |

### CloudFlare Workers反代代码（支持VLESS\VMESS\Trojan-Go的WS模式，可分别用两个账号的应用程序名（UUID与path保持一致），单双号天分别执行，那一个月就有550+550小时）

1.适用单一应用的反代代码

```
addEventListener(
  "fetch", event => {
    let url = new URL(event.request.url);
    url.host = "appname.herokuapp.com";
    let request = new Request(url, event.request);
    event.respondWith(
      fetch(request)
    )
  }
)
```

2.适用单双日循环执行的反代代码

```
const SingleDay = '应用程序名1.herokuapp.com'
const DoubleDay = '应用程序名2.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        if (nd.getDate()%2) {
            host = SingleDay
        } else {
            host = DoubleDay
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

3.适用多实例循环执行的反代代码

```
const Day0 = 'app0.herokuapp.com'
const Day1 = 'app1.herokuapp.com'
const Day2 = 'app2.herokuapp.com'
const Day3 = 'app3.herokuapp.com'
const Day4 = 'app4.herokuapp.com'
addEventListener(
    "fetch",event => {
    
        let nd = new Date();
        let day = nd.getDate() % 5;
        if (day === 0) {
            host = Day0
        } else if (day === 1) {
            host = Day1
        } else if (day === 2) {
            host = Day2
        } else if (day === 3){
            host = Day3
        } else if (day === 4){
            host = Day4
        } else {
            host = Day1
        }
        
        let url=new URL(event.request.url);
        url.hostname=host;
        let request=new Request(url,event.request);
        event. respondWith(
            fetch(request)
        )
    }
)
```

### 原作者项目地址：https://github.com/mixool/xrayku

# 鸣谢

- [Xrayku](https://github.com/mixool/xrayku)
- [Project V](https://github.com/v2fly/v2ray-core.git)
- [Project X](https://github.com/XTLS/Xray-core.git)
- [HeroKu](https://heroku.com)
- [heroku-vless](https://github.com/DanyTPG/heroku-vless.git)
- [Better Cloudflare IP](https://github.com/badafans/better-cloudflare-ip.git)
- [CloudflareSpeedTest](https://github.com/XIU2/CloudflareSpeedTest.git)
- [CloudflarespeedTest-Rust](https://github.com/lixiang810/CloudflareSpeedTest-Rust.git)
