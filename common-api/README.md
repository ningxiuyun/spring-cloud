README
===========================
几个子项目共用的接口和类。

提供一个接口，供sample-service和feign-client两个项目共用。

## 依赖此项目的项目
|名称 | 用途 |
|:-- |:-- |
|[sample-service](../sample-service)  [feign-client](../feign-client) | FeignClient在调用方和被调用方都使用一个同一的接口 |