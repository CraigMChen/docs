# 制品

## 创建制品
创建制品前请先完成项目的集群设置和分支规则配置。

* 进入 **DevOps 平台 > 项目 > 项目设置 > 通用设置 > 集群设置** 设置集群。

* 进入 **DevOps 平台 > 项目 > 项目设置 > 代码设置 > 分支规则** 创建分支规则。

目前制品仅支持通过 Release Action 创建。

![](https://terminus-paas.oss-cn-hangzhou.aliyuncs.com/paas-doc/2021/08/23/5a492871-c40d-4e5d-8ee5-d45269a5b015.png)

1. 进入 **DevOps 平台 > 项目 > 应用 > 代码仓库 > 代码浏览**，创建流水线文件，添加 Action（任务类型 > 应用打包发布制品）并填写配置参数。

2. 进入 **DevOps 平台 > 项目 > 应用 > 流水线**，选择分支和流水线，点击 **新建流水线**，完成构建后执行流水线。

3. 流水线执行成功即代表制品创建成功。

流水线将根据所在分支匹配分支规则，确认制品部署环境。

## 查看制品

进入 **DevOps 平台 > 项目 > 应用 > 制品管理**，可根据分支或关键字搜索制品。

选择制品后可查看制品信息，包括所属集群、分支、应用、创建人、操作人、创建时间、提交 ID、erda.yml。

![](https://terminus-paas.oss-cn-hangzhou.aliyuncs.com/paas-doc/2021/08/23/d17563cc-b4bc-4004-b070-9712f19c7e75.png)

## 更新制品

仅支持编辑制品描述，其余信息不可修改。

![](https://terminus-paas.oss-cn-hangzhou.aliyuncs.com/paas-doc/2021/08/23/9bb491f4-7921-4216-a898-b07f5bc47770.png)

## 删除制品

制品的 erda.yml 定义了制品引用的 Docker Image 信息，制品过期时间由环境变量 RELEASE_MAX_TIME_RESERVED 决定，默认为 3 天。

集群将于每天零点搜索已过期且 Version 为空的未部署制品，删除制品存储的 Image 信息。若该制品下的 Image 未被其他制品使用，则删除 Image Manifest，删除成功后再删除制品。





