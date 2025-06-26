## vArmor <https://github.com/bytedance/vArmor>
<!--auto_detail_badge_begin_0b490ffb61b26b45de3ea5d7dd8a582e-->
![Language](https://img.shields.io/badge/Language-Golang-blue)
![Author](https://img.shields.io/badge/Author-bytedance-orange)
![GitHub stars](https://img.shields.io/github/stars/bytedance/vArmor.svg?style=flat&logo=github)
![Version](https://img.shields.io/badge/Version-V0.8.0-red)
![Time](https://img.shields.io/badge/Join-20230831-green)
<!--auto_detail_badge_end_fef74f2d7ea73fcc43ff78e05b1e7451-->

vArmor 是一个云原生容器沙箱系统，它借助 Linux 的 [AppArmor LSM](https://en.wikipedia.org/wiki/AppArmor), [BPF LSM](https://docs.kernel.org/bpf/prog_lsm.html) 和 [Seccomp](https://en.wikipedia.org/wiki/Seccomp) 技术实现强制访问控制器（即 enforcer），从而对容器进行安全加固。它可以用于增强容器隔离性、减少内核攻击面、增加容器逃逸或横行移动攻击的难度与成本。

您可以借助 vArmor 在以下场景对 Kubernetes 集群中的容器进行沙箱防护
* 业务场景存在多租户（多租户共享同一个集群），由于成本、技术条件等原因无法使用硬件虚拟化容器（如 Kata Container）
* 需要对关键的业务进行安全加固，增加攻击者权限提升、容器逃逸、横向渗透的难度与成本
* 当出现高危漏洞，但由于修复难度大、周期长等原因无法立即修复时，可以借助 vArmor 实施漏洞利用缓解（具体取决于漏洞类型或漏洞利用向量。缓解代表阻断利用向量、增加利用难度）

*注意：如果需要高强度的隔离方案，建议优先考虑使用硬件虚拟化容器（如 Kata Container）进行计算隔离，并借助 CNI 的 NetworkPolicy 进行网络隔离。*

**vArmor 的特色**
* **Cloud-Native**. vArmor 遵循 Kubernetes Operator 设计模式，用户可通过操作 [CRD API](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/) 对特定的 Workloads 进行加固。从而以更贴近业务的视角，实现对容器化微服务的沙箱加固。
* **Multiple Enforcers**. vArmor 将 AppArmor、BPF、Seccomp 抽象为 Enforcer，并支持单独或组合使用，从而对容器的文件访问、进程执行、网络外联、系统调用等进行访问控制。
* **Allow-by-Default**. vArmor 当前重点支持此安全模型。即只有显式声明的行为会被阻断，从而减少性能损失和增加易用性。
* **Built-in Rules**. vArmor 提供了一系列开箱即用的内置规则。这些规则为 Allow-by-Default 安全模型设计，从而极大降低对用户专业知识的要求。
* **Behavior Modeling**. vArmor 支持对工作负载进行行为建模。这可用于开发白名单安全策略、分析哪些内置规则可用于加固应用、指导工作负载的配置遵循权限最小化原则。
* **Deny-by-Default**. vArmor 可以基于行为模型创建白名单安全策略，从而确保仅显式声明的行为被允许。

vArmor 由字节跳动终端安全团队的 **Elkeid Team** 研发，目前该项目仍在积极迭代中。


## 文档
您可以访问 [varmor.org](https://varmor.org) 查看 vArmor 的文档。

👉 **[快速上手](https://www.varmor.org/docs/introduction#quick-start)**

👉 **[安装指引](https://www.varmor.org/docs/getting_started/installation)**

👉 **[使用手册](https://www.varmor.org/docs/getting_started/usage_instructions)**

👉 **[策略与规则](https://www.varmor.org/docs/guides/policies_and_rules)**

👉 **[性能说明](https://www.varmor.org/docs/guides/performance)**


## 贡献
感谢您有兴趣为 vArmor 做出贡献！以下是帮助您入门的一些步骤：

✔ 阅读并遵循社区[行为准则](https://github.com/bytedance/vArmor/blob/main/CODE_OF_CONDUCT.md).

✔ 阅读[开发指引](https://github.com/bytedance/vArmor/blob/main/docs/development_guide.md).

✔ 加入 vArmor [飞书群](https://applink.larkoffice.com/client/chat/chatter/add_by_link?link_token=ae5pfb2d-f8a4-4f0b-b12e-15f24fdaeb24&qr_code=true).

<!--auto_detail_active_begin_e1c6fb434b6f0baf6912c7a1934f772b-->
## 项目相关


## 最近更新

#### [v0.8.0] - 2025-06-26

**新增**  
- 添加了自托管运行器和 BPF 执行者的端到端测试用例  
- 支持为网络出口规则定义多个端口和端口范围  
- 添加了 PodServiceEgressControl 特性，限制对 Pod 和服务的访问  
- 添加了 pod-self 实体，以限制容器访问其所在 Pod 的 IP  
- 添加了一个未指定的实体，以限制容器访问 0.0.0.0 和 ::  
- 添加了一个 localhost 实体，以限制容器访问回环地址  
- 通过灵活的配置文件来源和观察支持增强了深入防御模式  
- 从 Pod 注释中提取了配置文件名称，并将其添加到违规事件中，以改善日志可追溯性  
- 支持将元数据注入违规事件  
- 支持从现有策略中移除 BPF 执行者  
- 添加了 block-access-to-kube-apiserver 内置规则  
- 添加了 ingress-nightmare-mitigation 内置规则  
**更新**  
- 将 AppArmor 和 Seccomp 配置文件以纯文本形式保存至 CR 对象  
- 增强了状态同步的并发安全性  
- 从 CRD 定义中提取公共字段到一个公共文件  
- 升级 libseccomp-golang 至 v0.11.0  
- 改进了 ArmorProfile 处理中的错误处理，以收集所有配置文件错误  
 -为 Kubernetes 客户端设置默认的 qps 和突发值  
- 将 MaxTargetContainerCountForBpfLsm 的值从 100 增加到 110

#### [v0.7.1] - 2025-04-23

**更新**  
- 修复了 procfs 中的路径匹配问题，以确保 FD 匹配正确  
- 修复了 disallow-load-bpf-via-setsockopt 规则中对合法 setsockopt 调用的错误拦截

#### [v0.7.0] - 2025-02-27

**新增**  
- 在 VarmorPolicy 和 VarmorClusterPolicy CRD 中添加了 AllowViolations 字段  
- AppArmor、BPF 和 Seccomp enforcers 支持观察模式  
- 在 debug 日志中将未被阻止的违规事件记录到 violence.log 文件中  
- 在 ArmorProfileModel CRD 中添加了 StorageType 字段  
- 在 ArmorProfileModel 资源的附加打印机列中添加了 STORAGE-TYPE 字段  
- 在启用行为建模功能时，将 emptyDir 数据卷挂载到 agent 和管理器  
- 当 ArmorProfileModel 对象超出限制时，管理器将行为数据和配置文件保存到数据卷内的本地文件中- agent 建模期间将审计数据缓存在数据卷中  
- 支持从管理器的接口导出完整的 ArmorProfileModel 对象  
- 管理器的所有接暴露在 /apis 路径  
- 添加了 --logFormat 命令行选项，并允许以 JSON 格式输出日志  
- 修改了 VarmorPolicy 和 VarmorClusterPolicy CRD 的 AppArmorRawRules 结构  
- 当遇到不符合标准的个人信息时强制定期更新  
- 当策略在 DefenseInDepth 模式下运行时，如果 ArmorProfileModel 对象的 StorageType 字段为 LocalDisk，则从本地文件加载配置文件  
- 添加了 --set jsonLogFormat.enabled=true 选项，用于将日志格式切换为 JSON  

**修复**  
- 如果 agent 不在容器中，readinessProbe 使用默认端口 6080  
- 当 agent 在容器中运行时，通过 varmor-classifier-svc 服务访问分类器  
- 增加了超时重试的等待时间  
- 将 trace 的日志级别从 3 切换到 2

#### [v0.6.3] - 2025-02-19

**更新**  
- 为 Seccomp enforcer 添加了 disallow-load-bpf-via-setsockopt 内置规则  
- 为 Seccomp enforcer 添加了 disallow-userfaultfd-creation 内置规则  
- 增加了状态报告超时重试的等待时间

#### [v0.6.2] - 2024-12-27

**更新**  
- 新增在行为建模过程中，将其 mnt ns id 添加到监视列表中  
- 优化当行为数据太大时直接返回  
- 添加了调试标志  
- 为 Seccomp 执行器添加了 disallow-load-all-bpf-prog 规则  
- 修复在安装 varmor 的命名空间中创建 varmor-classifier-svc 服务

<!--auto_detail_active_end_f9cf7911015e9913b7e691a7a5878527-->
