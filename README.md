# nwcd-mirror
在AWS中国区域上提供常见开源的镜像数据源


## Release Notes
1. 提供以下镜像加速地址<br>
   - docker-hub加速镜像: https://dockerhub.mirror.nwcdcdn.cn
   - gcr.io加速镜像: https://gcr.mirror.nwcdcdn.cn
   - quay.io加速镜像: https://quay.mirror.nwcdcdn.cn
2. 高可用保障: AWS中国宁夏区域多可用区域部署
2. 访问限制: 仅限AWS中国区域访问使用

## 计划
* [X] 域名证书获取
* [ ] 增加docker.io镜像+测试
* [ ] 增加gcr.io镜像+测试
* [ ] 增加quay.io镜像+测试
* [ ] NLB 2 AZ 支持
* [ ] AWS中国区域访问限制配置(结合ip-range notification+lambda+update subnet Network Acl)
