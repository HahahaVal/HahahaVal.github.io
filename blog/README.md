# 安装golang
sudo yum -y install golang

# 添加epel repo
sudo vim /etc/yum.repos.d/hugo.repo
```shell
[daftaupe-hugo]
name=Copr repo for hugo owned by daftaupe
baseurl=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/epel-7-$basearch/
type=rpm-md
skip_if_unavailable=True
gpgcheck=1
gpgkey=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/pubkey.gpg
repo_gpgcheck=0
enabled=1
```

# 安装hugo
sudo yum -y install hugo

# 创建一个新网站
hugo new site blog

# 添加一个主题
```shell
cd blog
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
```

# 在根目录下的 config.toml 文件中添加一行
echo 'theme = "ananke"' >> config.toml

# 添加一个文章
hugo new posts/my-first-post.md  
通过命令行创建的文章会自动生成一部分文本,需要把draft:true修改成draft:false才可以上传这篇文章  

# 配置github
Setting页面修改Source的选项为master branch /docs folder：

# 修改配置文件 config.toml
Setting页面找到Github Pages 的域名地址替换config.toml文件的baseUrl

# 启动hugo服务器
hugo server -D

# 打包网站到/docs
hugo -d docs