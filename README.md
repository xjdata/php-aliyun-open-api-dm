The DM SDK for Aliyun OpenAPI
==============================

The DM SDK for Aliyun OpenAPI

基于Lokielse[https://github.com/lokielse/php-aliyun-open-api-core]

## Install

Via Composer

``` bash
$ composer require xjdata/aliyun-open-api-dm
```

## Usage

```php
/**
 * 访问信息
 */
$config = [
	'AccessKeyId'=>'<your access_key_id>',
	'AccessKeySecret'=>'<your access_key_secret>',
];

/**
 * 配置网关
 */
$endpoint = new Endpoint('cn-hangzhou', EndpointConfig::getRegionIds(), EndpointConfig::getProductDomains());
EndpointProvider::setEndpoints([ $endpoint ]);

/**
 * 授权资料
 */
$profile = DefaultProfile::getProfile('cn-hangzhou', $config['AccessKeyId'], $config['AccessKeySecret']);


/**
 * 请求对象
 */
$request = new \Aliyun\Dm\Request\SingleSendMailRequest();
$request->setAccountName("notice-no-reply@sendmail.aliyun.xxx.com");
$request->setFromAlias("某某");
$request->setAddressType(1);
$request->setTagName("youtagname");
$request->setReplyToAddress("true");
$request->setToAddress("xxx@qq.com");
$request->setSubject("邮件主题");
$request->setHtmlBody("邮件正文");
$response = $client->getAcsResponse($request);
var_dump($response);
```

[官方文档](https://help.aliyun.com/document_detail/directmail/api-reference/overview.html)