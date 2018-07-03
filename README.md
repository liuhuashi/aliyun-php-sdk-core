# aliyun-php-sdk-core

---

阿里云 PHP SDK，用于创建并初始化DefaultAcsClient实例。

## 环境准备

使用阿里云PHP SDK，您需要：

- RAM帐号
- AccessKey ID
- AccessKey Secret

[查看AccessKey](https://usercenter.console.aliyun.com/?spm=a2c4g.11186623.2.1.NM8Qvq#/manage/ak)

## 如何使用阿里云PHP SDK

调用阿里云PHP SDK的3个主要步骤:

- 创建并初始化DefaultAcsClient实例。

在创建DefaultAcsClient实例并初始化时，您需要提供Region ID,AccessKey ID,AccessKey Secret这三个参数的值。

- 创建API请求并设置参数。
- 发起请求并处理应答或异常。

## 实例
 
```php
<?php

use Ecs\Request\V20140526\DescribeInstancesRequest;

# 创建DefaultAcsClient实例并初始化
$clientProfile = DefaultProfile::getProfile(
    "<your-region-id>",                   # 您的 Region ID 
    "<your-access-key-id>",               # 您的 AccessKey ID
    "<your-access-key-secret>"            # 您的 AccessKey Secret
);
$client = new DefaultAcsClient($clientProfile);

# 创建API请求并设置参数
$request = new DescribeInstancesRequest();
$request->setPageSize(10);

# 发起请求并处理返回
try {
    $response = $client->getAcsResponse($request);
    print_r($response);
} catch(ServerException $e) {
    print "Error: " . $e->getErrorCode() . " Message: " . $e->getMessage() . "\n";
} catch(ClientException $e) {
    print "Error: " . $e->getErrorCode() . " Message: " . $e->getMessage() . "\n";
}
?>
```
