---
---

# 替换 gems 默认源

此处的帮助文档已经废弃，新的内容请访问 <https://mirrors.ustc.edu.cn/help/>

---

    gem sources  #列出默认源
    gem sources --remove https://rubygems.org/  #移除默认源
    gem sources -a https://mirrors.ustc.edu.cn/rubygems/  #添加科大源

---

# 替换 Rails 默认源

    cd path/to/your/project
    #Linux only:
    sed -i "/^source/c source 'http://mirrors.ustc.edu.cn/rubygems/'" Gemfile
    #OS X only:
    sed -ig "s/^source.*/source 'http:\\/\\/mirrors.ustc.edu.cn\\/rubygems\\/'/g" Gemfile
