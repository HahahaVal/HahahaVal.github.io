# 安装golang
sudo yum -y install golang

``
``shell
# 添加epel repo
sudo vim /etc/yum.repos.d/hugo.repo
``shell
[daftaupe-hugo]
name=Copr repo for hugo owned by daftaupe
baseurl=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/epel-7-$basearch/
type=rpm-md
skip_if_unavailable=True
gpgcheck=1
gpgkey=https://copr-be.cloud.fedoraproject.org/results/daftaupe/hugo/pubkey.gpg
repo_gpgcheck=0
enabled=1
``

# 安装hugo
sudo yum -y install hugo

# 创建一个新网站
hugo new site quickstart

# 添加一个主题
``shell
cd quickstart
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
``

# 在根目录下的 config.toml 文件中添加一行
echo 'theme = "ananke"' >> config.toml

# 添加一个文章
hugo new posts/my-first-post.md

# 启动hugo服务器
hugo server -D
