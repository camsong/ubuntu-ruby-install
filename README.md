```shell
#如果是使用vmware，可直接在这里下载配置好的操作系统，有Ubuntu,Centos,Fedora,SuSE等
#http://www.vmware.com/appliances/directory/cat/508
#我下载的是这个：http://www.vmware.com/appliances/directory/1259373
#下面开始安装
#备份源
sudo mv /etc/apt/sources.list /etc/apt/sources.list.back
#换源，我感觉163的源快又稳定
sudo wget https://raw.github.com/gist/1588527/25ff324c76b25a788f8b689921973cd66a7110a9/sources.list -O /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
#chrome浏览器
sudo apt-get install chromium-browser

#安装所有linux包
sudo apt-get install build-essential bison openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev  libxml2-dev libxslt-dev autoconf libc6-dev zlib1g-dev libssl-dev build-essential curl git-core libc6-dev g++ gcc ncurses-dev graphicsmagick libmagick9-dev
#install latest development state:
bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer )
#添加rvm环境变量，只需要运行一次
source .bashrc
rvm install 1.9.2
rvm 1.9.2 --default
#or sometimes we will get:no such file to load -- openssl (LoadError)
cd ~/.rvm/src/ruby-1.9.2-*/ext/openssl
ruby extconf.rb
make && make install
#irb should support readline. rmagick need.
cd ~/.rvm/src/ruby-1.9.2-*/ext/readline
ruby extconf.rb
make && make install
#vim编辑神器
sudo apt-get install vim 
#vim-ruby don't have a source

#安装node.js
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs

#安装zsh
sudo apt-get install zsh
#引入增强插件包on-my-zsh,支持git,rails等补全，可选多种外观皮肤
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
#zsh作为默认shell，重启后生效
chsh -s /bin/zsh
#修改~/.zshrc，打开一些需要的plugin
#plugins=(command-not-found git rails3 ruby bundler heroku)

#具体有哪些补全功能呢，可以查看列表
#-h不列出文件名
grep -h -r -e '^alias' ~/.oh-my-zsh
```
