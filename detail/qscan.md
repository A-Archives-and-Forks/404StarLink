## qscan <https://github.com/qi4L/qscan>
<!--auto_detail_badge_begin_0b490ffb61b26b45de3ea5d7dd8a582e-->
![Language](https://img.shields.io/badge/Language-Go-blue)
![Author](https://img.shields.io/badge/Author-qi4L-orange)
![GitHub stars](https://img.shields.io/github/stars/qi4L/qscan.svg?style=flat&logo=github)
![Version](https://img.shields.io/badge/Version-V1.8.2-red)
![Time](https://img.shields.io/badge/Join-20250513-green)
<!--auto_detail_badge_end_fef74f2d7ea73fcc43ff78e05b1e7451-->

<p align="center"> 一个速度极快的内网扫描器，具备端口扫描、协议检测、指纹识别，暴力破解，漏洞探测等功能。支持协议1200+，协议指纹10000+，应用指纹20000+，暴力破解协议10余种 </p>

<p align="center"> 中文文档 | <a href="README.en.md">English</a> </p>

# 🚀 上手指南

📢 请务必花一点时间阅读此文档，有助于你快速熟悉JYso！

🧐 使用文档[Wiki](https://github.com/qi4L/qscan/wiki)。

✔ 下载最新版本的[Releases](https://github.com/qi4L/qscan/releases)。

# 👍 特点

+ spy 模式极速遍历常见B段，比常见的一个一个遍历，快上很多倍；
+ 在精确识别端口的同时，又拥有极快的速度；
  + 线程池优化：减少内存分配和 GC 开销；
  + 模板缓存：减少重复构建；
  + 并行发送：榨干多核 CPU；
  + 批量处理：减少系统调用；
  + 并行处理管道： 接收、解析、处理三阶段并行，效率最大化；
  + 缓冲区优化: 增加 Channel 缓冲区，避免阻塞；

# 和Fscan对比的优势

+ 同端口数，同线程数下的速度对比：

QScan
![img.png](https://raw.githubusercontent.com/qi4L/qscan/master/assets/qscan速度.png)

FScan
![img.png](https://raw.githubusercontent.com/qi4L/qscan/master/assets/FScan.png)

<!--auto_detail_active_begin_e1c6fb434b6f0baf6912c7a1934f772b-->
## 项目相关


## 最近更新

#### [v1.8.2] - 2026-05-24

 - 大量优化，exp并发不占用port和url并发组  


#### [v1.8.1] - 2025-11-27

 ** 修复BUG issues 20 ** 


<!--auto_detail_active_end_f9cf7911015e9913b7e691a7a5878527-->
