# miniguiinstall
## 1：安装Ubuntu系统（虚拟机或双系统）

#### 目前使用的是Ubuntu 16.04 LTS

#### 系统下载地址：[点击此处](https://releases.ubuntu.com/)

## 2：使用终端复制下面的指令执行，导入必须使用的软件包和依赖库（目前使用的是MiniGUI 4.0）（[点击此处](https://minigui.fmsoft.cn/zh/blog/quick-start)）
```bash
sudo apt install git gcc g++ binutils autoconf automake libtool make cmake pkg-config libgtk2.0-dev libjpeg-dev libpng12-dev libfreetype6-dev libinput-dev libdrm-dev libsqlite3-dev libxml2-dev electric-fence libssl-dev
```
## 3：配置Ubuntu的Git设置，后期拉取代码需要（[点击此处](https://blog.csdn.net/Akutamatsu/article/details/132368481)）

**【Step.1】**[安装](https://so.csdn.net/so/search?q=安装&spm=1001.2101.3001.7020) git，第2步安装了就无需再执行

```bash
sudo apt install git
```

安装完成后执行下句，可以看到安装版本：

```bash
git --version
```

**【Step.2】**配置邮箱 ([git](https://so.csdn.net/so/search?q=git&spm=1001.2101.3001.7020)网站账户注册的邮箱，如bob2023@yy.com) 和用户名 (任取，如bob)：

```bash
git config --global user.email "bob2023@yy.com"



git config --global user.name "bob"
```

随后可执行下句，查看是否配置成功：

```bash
git config --list
```

【**Step.3**】生成 [SSH](https://so.csdn.net/so/search?q=SSH&spm=1001.2101.3001.7020) 密钥，用于远程访问 git (下面使用的公钥算法是 ed25519)：

```bash
ssh-keygen -t ed25519 -C "bob2023@yy.com"
```

【**Step.4**】在 git 上注册所生成密钥中的公钥数据，如上图所示，执行：

```bash
cat /home/zzd/.ssh/id_ed25519.pub
```

**【Step.5】**到 Git 网站个人账户信息中，注册 SSH 公钥。

## 4：编译minigui环境（[点击此处](https://minigui.fmsoft.cn/zh/blog/quick-start)）

    1. 从 GitHub clone `build-minigui-4.0` 存储库:

   ```
    $ git clone git@github.com:VincentWei/build-minigui-4.0.git
    $ cd build-minigui-4.0
   ```

    2. 将 `config.sh` 复制到 `myconfig.sh` 并编辑 `myconfig.sh` 以满足您的需求：

   ```
    $ cp config.sh myconfig.sh
   ```

    3. 运行 `fetch-all.sh` 从 GitHub 获取所有源代码：

   ```
    $ ./fetch-all.sh
   ```

    4. 运行 `build-deps.sh` 构建并安装 gvfb、chipmunk 和 harfbuzz：

   ```
    $ ./build-deps.sh
   ```

    5. 运行 `build-all.sh` 来构建所有:

   ```
    $ ./build-all.sh
   ```

    6. 运行 `mguxdemo`:（生成了mguxdem执行文件代表本地环境成功）

   ```
    $ cd /usr/local/bin
    $ ./mguxdem
   ```

## 5：安装Eclips环境（本处介绍的Ubuntu系统的Eclips环境）
### 1：安装Eclips需要的环境
```
sudo apt-get install eclipse eclipse-cdt g++
sudo  apt-get  install build-essential
sudo apt install default-jdk
```
### 2：安装minigui需要的环境
```
wget -qO - http://files.fmsoft.cn/ubuntu/key/fmsoft.gpg | sudo apt-key add -
Add the following line to /etc/apt/sources.list:
deb http://files.fmsoft.cn/ubuntu/ xenial restricted
sudo apt update
sudo apt install libminigui-ths-dev
sudo apt install ministudio
```

### 3：下载Eclips软件和插件

####  安装Eclipse
    请访问 eclipse 网站http://www.eclipse.org，了解安装 Eclipse 的详细信息。
    CDT 9.3 或更高版本：http://www.eclipse.org/cdt/
    Eclipse SDK 4.7.2 或更高版本：http://download.eclipse.org/eclipse/downloads/

#### 安装miniStudio的Eclipse插件
```
wget http://files.fmsoft.cn/ubuntu/eclipse-plugin/ministudio-eclipse-plugin-1.2.1.tar.gz
tar xvf ministudio-eclipse-plugin-1.2.1.tar.gz
```

#### 将文件从ministudio-eclipse-plugin目录复制到eclipse/dropins.后者是Eclipse插件所在的目录：
```
cp ministudio-eclipse-plugin-1.2.1/org.minigui.eclipse.cdt.mstudio_1.2.1.jar /usr/share/eclipse/dropins/
```
