---
---

# AOSC OS 镜像源使用帮助

此处的帮助文档已经废弃，新的内容请访问 <https://mirrors.ustc.edu.cn/help/>

---

anthon 为 [AnthonOS](https://anthonos.org/ "https://anthonos.org") 项目的官方源 [http://repo.anthonos.org](http://repo.anthonos.org/ "http://repo.anthonos.org") 的镜像。

## 快速设置

考虑到安同的系统情况可能时有改动，并且源也不少，我们就偷个懒：

anthon-apt.sh:

    # AOSC OSes, apt-dpkg
    cat /etc/apt/sources.list | egrep 'mirror|repo' |
    sed -r -e 's@(mirror|repo).anthonos.org@mirrors.ustc.edu.cn/anthon@g' >> /etc/apt/sources.list

如果你只想用 USTC 镜像的话，勇敢地把 `>>` 改成 `>` 吧。由于 AOSC OS3 yum 暂时没有 fastestmirror，你需要做一些砍手的工作：

anthon-yum.sh:

    # AOSC OS3, yum-rpm
    sudo sed -r -e -i.orig 's@(mirror|repo).anthonos.org@mirrors.ustc.edu.cn/anthon@g' /etc/yum/repos.d/aosc.repo

接下来是分系统信息：

## AOSC OS2

AOSC OS2 具有多个仓库，均位于 [/anthon/os2-repo](https://mirrors.ustc.edu.cn/anthon/os2-repo "https://mirrors.ustc.edu.cn/anthon/os2-repo") 下。

sources-os2.list:

    # /etc/apt/sources.list
    deb http://mirrors.ustc.edu.cn/anthon/os2-repo/os2/ # OS2 基础源
    deb http://mirrors.ustc.edu.cn/anthon/os2-repo/os2-anthonos/ # OS2 AnthonOS 源
    deb http://mirrors.ustc.edu.cn/anthon/os2-repo/os2-apps/ # OS2 Apps 半实验源
    ## 不常见的
    # deb http://mirrors.ustc.edu.cn/anthon/os2-repo/os2-centralpoint/ # OS2 CentralPoint 服务器源
    # deb http://mirrors.ustc.edu.cn/anthon/os2-repo/os2-studio/ # OS2 Studio 源

---

## AOSC OS3

AOSC OS3 的 deb 和 rpm 仓库在试验阶段存于 [/anthon/os3-next](https://mirrors.ustc.edu.cn/anthon/os3-next/ "https://mirrors.ustc.edu.cn/anthon/os3-next/")。

#### deb 仓库配置

sources-os3.list:

    # /etc/apt/sources.list
    deb http://mirrors.ustc.edu.cn/anthon/os3-next/os3-dpkg/ # 主源

#### rpm 仓库配置

aosc.repo:

    # /etc/yum/repos.d/aosc.repo
    [Official]
    name=AOSC OS3
    baseurl=http://mirrors.ustc.edu.cn/anthon/os3-next/os3-rpm/
    enabled=1

#### Zypper 用户

    zypper ar http://mirrors.ustc.edu.cn/anthon/os3-next/os3-rpm "AOSC OS3"
    zypper refresh
