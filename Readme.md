# clash 订阅工具

## 原理

订阅链接解析为clash配置文件，然后通过js脚本处理可以实现自定义分组规则等。

clash订阅1,clash订阅2 -> 合并订阅 -> 处理脚本1,处理脚本2 -> 新的订阅

建议使用场景：
1. 订阅合并，例如：多个订阅合并成一个订阅，方便管理。
2. 自定义规则
3. 自定义分组
4. 手机电脑路由器规则全部使用同一个配置，实现集中维护


## 部署方式
本项目使用docker发布，详细部署方式请查看[docker-compose.yml](./docker-compose.yml) 文件。

可以本地部署内网使用，注意发布到公网需要部署nginx配置好nginx证书保证没有中间人攻击。

## JS脚本格式

````javascript
/**主方法 */
function main(configJsonStr) {
  const configObjClone = JSON.parse(configJsonStr);
  //对configObjClone进行修改
    configObjClone.rules = [
        'GEOIP,CN,DIRECT'
        // ...
    ]
  return JSON.stringify(configObjClone);
}
````

## 系统截图
登陆页面 默认 admin/123456
![登陆](./sys-img/login.png)
修改密码
![修改密码](./sys-img/password.png)
节点来源管理
![节点来源管理](./sys-img/proxy-node.png)
脚本管理
![脚本管理](./sys-img/script.png)
订阅管理
![订阅管理](./sys-img/sub.png)