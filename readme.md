# vagrant-centos7-dev
用于开发的 centos7.5 环境

## 主要配置
- vbox 基础配置
  - 2 core CPU
  - 2G RAM
  - 40G HDD
- 插件
  - vagrant-share
  - vagrant-vbguest
  - vagrant-disksize

## Usage


### for Mac OS HomeBrew

#### 安装 virtualbox
```
# mac os verison < 10.13
brew cask install virtualbox
# 更高版本由于安全限制，需要通过安装包 gui 安装，
# 下载地址： https://www.virtualbox.org/wiki/Downloads
# 启动安全限制：https://blogs.oracle.com/scoter/getting-oracle-vm-virtualbox-correctly-installed-on-macos-1014-mojave
```

#### 安装 vagrant
```
brew cask install vagrant
```

```
git clone https://github.com/hectorqiu/vagrant-centos7-dev.git
cd vagrant-centos7-dev
vagrant up
```


## 国内 vagrant box 下载慢解决办法

#### 通过 Makefile 下载配置（推荐）
```
make add_box
```

