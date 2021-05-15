# 宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序

#### 1、简介

演示：https://img.yyhy.me

下载：https://git.code.tencent.com/yyhy/ImgBed.git



#### 2、准备

宝塔面板（宝塔服务器面板，一键全能部署及管理，送你3188元礼包，点我领取https://www.bt.cn/?invite_code=MV9ub2NxdmI=）

PHP版本7.2及以上

nginx或者Apache皆可

MySQL5.7



#### 3、下载及设置

首先需要clone程序，具体如下：

1）新建站点

宝塔新建站点略过

2）开始下载

用SSH工具连接服务器，输入以下命令：

```
git clone https://git.code.tencent.com/yyhy/ImgBed.gitchown -R www ImgBed  #改版所有者为wwwchmod -R 777 ImgBed  #设置权限为755
```

注意，这个程序放置在腾讯工蜂，所以你需要登录之后设置好用户名和密码才可以下载。



#### 4、安装设置

**1）新建数据库**

宝塔面板新建数据库略过

**2）设置运行目录为/Public**

网站设置→网站目录，具体看图：

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-1.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-1.png)

**3）设置伪静态**

Apache无需配置，nginx伪静态规则在程序根目录有个nginx.txt，复制规则配置即可，之后给所有目录777权限。伪静态规则如下：

如何放置看图：

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-2.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-2.png)

**4）设置权限**

所有目录777权限。

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-3.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-3.png)

**5）配置/App/Database.php内的数据库信息**

根据自己新建的数据库信息来更新以下信息。

```
return [
    'default' => 'mysql',
    'connections' => [
        'mysql' => [
            // 数据库类型
            'type' => 'mysql',
            // 服务器地址
            'hostname' => '127.0.0.1',
            // 数据库名
            'database' => 'img',
            // 数据库用户名
            'username' => 'root',
            // 数据库密码
            'password' => 'root',
            // 数据库连接端口
            'hostport' => '3306',
            // 数据库连接参数
            'params' => [],
            // 数据库编码默认采用utf8
            'charset' => 'utf8',
            // 数据库表前缀
            'prefix' => 'img_',
        ],
    ],
];。
```

**6）导入数据库**

把程序内的 install.sql 和 update.sql 复制到 /www/backup/database 内。然后先导入 install.sql，打开网页 然后导入 update.sql 数据库。

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-4.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-4.png)



#### 5、打开网站

以上步骤都完成之后，我们就可以打开网站了，效果如图：

**1）前台**

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-5.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-5.png)

**2）后台**

后台登录地址：你的域名/admin/login

默认的用户名密码：admin  123456

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-6.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-6.png)



#### 6、Github配置

登录后台点开系统设置，找到Github配置。

**1）配置**

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-7.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-7.png)

关于这里的选项可以参考这篇文章：（[宝塔面板搭建autoPicCdn：一款基于jsdelivr+Github的免费CDN图床](https://www.daniao.org/10086.html)）

**2）测试**

保存之后，即可上传图片，如果不配置github，图片默认上传到自己的服务器。

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-8.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-8.png)

用这个地址打开后会跳转到https://cdn.jsdelivr.net/表示配置成功。

**3）鉴黄**

图床自带鉴黄，可以自行设置key

[![宝塔面板安装烟雨图床 – 一款带鉴黄功能的Github+JSDelivr的图床程序](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-9.png)](https://www.daniao.org/wp-content/uploads/2020/08/ImgBed-bt-9.png)



#### 7、最后

图床功能强大，可以开启游客或者关闭游客上传。

可以在后台管理图片，支持删除图片，这个到是很不错。

支持api，可以自行开发对接改api

如果，没有配置github，图床默认上传到服务器硬盘。

虽然默认是给出的图床域名，但是浏览器打开后会现实jsdelivr加速链接，用户可以自由选择。

