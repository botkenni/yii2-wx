<p align="center">
    <a href="https://nai8.me/yii2wx">
        <img src="https://nai8.me/images/yii2-wx-logo.png" height="150" alt="yii2-wx Logo"/>
    </a>
</p>
<p align="center">
    一款服务于yii2的微信SDK（公众号、小程序、开放平台和企业微信）
</p>
<p align="center">
    <img class="latest_stable_version_img" src="https://poser.pugx.org/abei2017/yii2-wx/v/stable">
    <img class="total_img" src="https://poser.pugx.org/abei2017/yii2-wx/downloads">
    <img class="latest_unstable_version_img" src="https://poser.pugx.org/abei2017/yii2-wx/v/unstable">
    <img class="license_img" src="https://poser.pugx.org/abei2017/yii2-wx/license">
</p>

<hr/>

<p align="center">
    感谢下面伙伴的支持
</p>
<p align="center">
    <a href="https://nai8.me">
        <img src="https://nai8.me/images/logo.png" height="90" alt="https://nai8.me"/>
    </a>
</p>
<p align="center">
    <img src="https://nai8.me/images/qrcodes/xiaobao-qrcode.jpg" height="180" alt="北哥小报"/>
</p>
<p align="center">
    除了代码，还有诗和远方。扫码关注我的公众号。
</p>

## 系统需求（Requirement）
- PHP >= 5.4
- Composer
- openssl
- fileinfo

## 安装（Installation）
```php
$ composer require "abei2017/yii2-wx" -vvv
```

## 配置（set）
配置参数建议存放到yii2的配置文件中，例如基础版yii2可以如下配置
```php
return [
    'wx'=>[
        //  公众号信息
        'mp'=>[
            //  账号基本信息
            'app_id'  => '', // 公众号的appid
            'secret'  => '', // 公众号的秘钥
            'token'   => '', // 接口的token
            'encodingAESKey'=>'',
            'safeMode'=>0,

            //  微信支付
            'payment'=>[
                'mch_id'        =>  '',// 商户ID
                'key'           =>  '',// 商户KEY
                'notify_url'    =>  '',// 支付通知地址
                'cert_path'     => '',// 证书
                'key_path'      => '',// 证书
            ],

            // web授权
            'oauth' => [
                'scopes'   => 'snsapi_userinfo',// 授权范围
                'callback' => '',// 授权回调
            ],
        ],

        //  小程序配置
        'mini'=>[
            //  基本配置
            'app_id'  => '', 
            'secret'  => '',
            //  微信支付
            'payment' => [
                'mch_id'        => '',
                'key'           => '',
            ],
        ]
    ]
];
```
对于配置，请不要修改数据的key值。

## 使用（use）
yii2-wx采用单一接口驱动功能的思路，比如下面的代码将生成一个微信带参数的二维码。

```php
use abei2017\wx\Application;

$conf = Yii::$app->params['wx']['mp'];
$app = new Application(['conf'=>$conf]);

$qrcode = $app->driver('mp.qrcode');
$data = $qrcode->intTemp(3600,9527);// 生成一个数字类临时二维码，有效期为3600秒
```

## 学习yii2-wx（learning yii2-wx）
北哥已将yii2-wx的配置和使用设计的简单易懂，因此通过文档和速查表你可以轻松的学会它，但是这也需要你之前对微信相关文档有所阅读，如果你是一名yii2或微信接口开发的初学者，我在自己的知识分享设置了一套针对性的视频课程（<a href="http://nai8.me/book/view.html?id=24" target="_blank">点击查看</a>），我想能让你零起步。

## 支持（Support）
- [yii2-wx速查表](https://nai8.me/tool/sc.html?id=2)
- [社区交流](https://nai8.me/forum/index.html?tags=108)

更多请参考 https://nai8.me/yii2wx

## 开源协议（License）
MIT