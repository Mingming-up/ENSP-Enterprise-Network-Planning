<div align="center">

# 🏢🌐 ENSP Enterprise Network Planning

### 基于华为 eNSP 的中大型企业网络规划、配置与验证实验

![Platform](https://img.shields.io/badge/Platform-Huawei_eNSP-E60012?style=flat-square)
![Network](https://img.shields.io/badge/Network-Enterprise_Lab-1677FF?style=flat-square)
![Protocol](https://img.shields.io/badge/Protocol-IPv4_%26_IPv6-6F42C1?style=flat-square)
![Status](https://img.shields.io/badge/Status-Learning_Project-2EA44F?style=flat-square)

从园区接入、双机冗余到总部—分部安全互联，完整复盘企业网络的规划、搭建、调试与优化过程。

[📖 项目简介](#project-intro) · [🗺️ 网络拓扑](#network-topology) · [🧩 技术模块](#technology-modules) · [🚀 快速开始](#quick-start) · [📁 仓库结构](#repository-structure)

</div>

---

<a id="project-intro"></a>

## 💡 项目简介

这是一个面向**企业网络学习与复盘**的华为 eNSP 综合实验项目。拓扑采用接入层、汇聚层、核心层的分层设计，并加入总部、分部、服务器区、无线网络、双出口防火墙及 ISP 网络等典型场景。

仓库不仅保存了可打开的 eNSP 拓扑工程，还提供了 **30 份设备导出配置**，方便对照拓扑理解交换、路由、WLAN、防火墙、VPN、IPv6 与可靠性技术如何协同工作。

> 🎯 **一句话概括：** 用一个完整的企业网仿真拓扑，把零散的数通知识串成可查看、可配置、可验证的综合实验。

<a id="network-topology"></a>

## 🗺️ 网络拓扑

![企业网络规划拓扑](assets/topology.png)

<div align="center">

🔗 园区内网 · 🏢 总部与分部 · 📶 双 AC 无线 · 🛡️ 双防火墙出口 · ☁️ ISP 网络

</div>

## ✨ 项目亮点

| | 实验场景 | 主要内容 |
| :---: | --- | --- |
| 🏗️ | 分层园区网络 | 接入、汇聚、核心三层架构，多部门 VLAN 与 Trunk 规划 |
| ♻️ | 高可用设计 | Eth-Trunk、MSTP、VRRP、BFD 及双机热备 |
| 🧭 | 动态路由 | OSPF、OSPFv3、RIP、IS-IS 与路由联动 |
| 📡 | 企业 WLAN | AP 上线、CAPWAP、业务下发与双 AC 备份 |
| 🛡️ | 出口与安全 | 防火墙安全策略、NAT、NAT Server、ACL 与 SSH |
| 🔐 | 总部分部互联 | GRE over IPsec VPN 与分支网络接入 |
| 🌍 | IPv6 与广域网 | DHCPv6、IPv6 over IPv4 GRE、MPLS/LDP |
| 🖥️ | 服务器区域 | HTTP、DNS 等业务节点与服务器负载分担实验 |

<a id="technology-modules"></a>

## 🧩 技术模块

```text
园区交换       VLAN / Trunk / Eth-Trunk / MSTP / 端口隔离
网关与可靠性   VRRP / BFD / 双机热备 / 链路检测
路由协议       OSPF / OSPFv3 / RIP / IS-IS
地址服务       DHCP / DHCP Relay / DHCPv6
无线网络       WLAN / AP / AC / CAPWAP / 双 AC 备份
出口安全       Firewall / NAT / NAT Server / ACL / SSH
广域互联       GRE over IPsec / IPv6 over IPv4 GRE / MPLS / LDP
```

<a id="quick-start"></a>

## 🚀 快速开始

### 1️⃣ 获取项目

```bash
git clone https://github.com/Mingming-up/ENSP-Enterprise-Network-Planning.git
cd ENSP-Enterprise-Network-Planning
```

### 2️⃣ 打开拓扑

在 Windows 中启动华为 eNSP，然后打开：

```text
Datacom-ENSP/Datacom-5.12.topo
```

> ⚠️ 请确保本机已正确安装 eNSP、VirtualBox 及拓扑所需设备组件。不同软件或设备版本可能导致工程启动、接口名称或部分命令表现存在差异。

### 3️⃣ 对照配置学习

进入 [`导出配置/`](导出配置/) 目录，可按设备角色查看配置：

- 🔀 `JR-SW*`、`HJ-SW*`、`HX-SW*`：接入、汇聚与核心交换设备
- 📶 `AC1.cfg`、`AC2.cfg`：无线控制器
- 🧱 `ZB-FW*`、`FB-FW*`：总部与分部防火墙
- ☁️ `ISP-AR*`：ISP 路由器
- 📬 `DHCP.cfg`、`DHCPv6-Server.cfg`：IPv4/IPv6 地址服务

### 4️⃣ 建议验证顺序

```mermaid
flowchart LR
    A["🔌 检查接口与 VLAN"] --> B["🔁 验证二层与网关冗余"]
    B --> C["🧭 检查路由邻居和路由表"]
    C --> D["📶 验证 WLAN 与地址获取"]
    D --> E["🛡️ 检查安全策略与 NAT"]
    E --> F["🔐 验证总部—分部互联"]
```

<a id="repository-structure"></a>

## 📁 仓库结构

```text
ENSP-Enterprise-Network-Planning/
├── 📂 Datacom-ENSP/
│   ├── Datacom-5.12.topo       # eNSP 拓扑工程
│   └── ...                      # 拓扑关联的设备运行文件
├── 📂 assets/
│   └── topology.png             # 完整网络拓扑图
├── 📂 导出配置/
│   ├── AC1.cfg / AC2.cfg        # 无线控制器配置
│   ├── ZB-FW*.cfg / FB-FW*.cfg # 防火墙配置
│   ├── ISP-AR*.cfg              # ISP 路由器配置
│   └── ...                      # 交换机与服务器相关配置
└── 📄 README.md
```

## 📚 适合谁学习？

- 🎓 正在学习华为数通、HCIA / HCIP 相关知识的同学
- 🧑‍💻 想把交换、路由、WLAN、防火墙和 VPN 串联起来练习的同学
- 🧰 需要企业网综合实验拓扑用于复盘、排障或面试准备的同学

## ⚠️ 项目边界

- 本项目基于 **eNSP 仿真环境**完成，主要用于学习、实验与配置复盘。
- 仿真结果不等同于真实生产网络交付；实际部署还需结合设备型号、VRP 版本、业务流量、安全要求和运维规范重新设计与验证。
- 拓扑与配置中如包含实验账号、地址或口令，仅适用于隔离的实验环境，请勿直接复用于真实网络。

## 🤝 交流与贡献

如果你发现配置问题，或希望补充验证步骤与实验说明，欢迎提交 [Issue](https://github.com/Mingming-up/ENSP-Enterprise-Network-Planning/issues) 或 Pull Request。

<div align="center">

⭐ 如果这个项目对你的学习有帮助，欢迎点一个 Star！

**Keep learning. Keep networking. 🚀**

</div>
