# nwcd-mirror
在AWS中国区域上提供常见开源的镜像数据源
1. 支持容器相关公开镜像仓库加速
2. 其他

## 免责申明
现在在测试阶段，仅限制测试使用。有相关问题，请提交issue，我们会及时处理。

## Release Notes
1. 提供以下镜像加速地址<br>
   - docker-hub加速镜像: 
     - HTTP支持: http://dockerhub.mirror.nwcdcdn.cn
     - HTTPS支持: https://dockerhub.mirror.nwcdcdn.cn
   - gcr.io加速镜像: 
     - HTTP支持: http://gcr.mirror.nwcdcdn.cn
     - HTTPS支持: https://gcr.mirror.nwcdcdn.cn
   - quay.io加速镜像: 
     - HTTP支持: http://quay.mirror.nwcdcdn.cn
     - HTTPS支持: https://quay.mirror.nwcdcdn.cn
2. 高可用保障: AWS中国宁夏区域多可用区域部署
3. 数据有效性：按需获取最新的公开容器镜像，并缓存30天
4. 访问限制: 仅限AWS中国区域访问使用

## Plan
* [X] 域名证书获取
* [X] 增加docker.io镜像+测试
* [X] 增加gcr.io镜像+测试
* [X] 增加quay.io镜像+测试
* [ ] NLB 2 AZ 支持
* [ ] AWS中国区域访问限制配置(结合ip-range notification+lambda+update subnet Network Acl)

## FAQ
Q1: 为什么要使用这些镜像?<br>
A1: 由于网络因素，docker或者k8s使用过程中，经常会用到的docker.io, gcr.io, quay.io 等公开容器仓库国内范围很慢或者直接不能访问。所以需要国内的相关镜像仓库或者自建私有仓库。为了增加AWS中国区域用户的使用体验，在AWS中国宁夏区域上就近搭建了镜像仓库。方便测试验证容器相关应用。

Q2: 我可以在生产环境中使用此镜像吗?<br>
A2: 本镜像由XXX提供运营支持，欢迎在测试中使用。生产环境，建议使用自有的托管镜像仓库，例如：[Amazon ECR](https://aws.amazon.com/cn/ecr/),构建生产环境。

Q3: 如何使用这些镜像，我需要做什么修改?<br>
A3: Docker-Hub 镜像修改
- Linux版本
    ```Bash
    sudo mkdir -p /etc/docker 
    sudo tee /etc/docker/daemon.json << EOF
    { "registry-mirrors": ["https://dockerhub.mirror.nwcdcdn.cn"] } 
    EOF 
    sudo systemctl daemon-reload 
    sudo systemctl restart docker
    ```

Q4: 我需要付费或者注册会员吗?<br>
A4: 此服务不收费，也无需注册会员认证。