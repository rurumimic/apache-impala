# Apache Impala

- [impala](https://impala.apache.org/)
  - [github](https://github.com/apache/impala)
  - [wiki](https://cwiki.apache.org/confluence/display/IMPALA/Impala+Home)
- cloudera
  - v6.3.0: [components](https://docs.cloudera.com/documentation/enterprise/6/release-notes/topics/rg_cdh_63_packaging.html)
  - github
    - [native-toolchain](https://github.com/cloudera/native-toolchain)
    - [impala-lzo](https://github.com/cloudera/impala-lzo)

## Build

### Scripts

```bash
impala/bin/bootstrap_build.sh
impala/buildall.sh
# impala/bin/report_build_error.sh
```

### Ubuntu 18.04

#### Vagrant

- IP Arbitrarily Picked: `192.168.63.20`

```bash
vagrant init ubuntu/bionic64
vagrant up
vagrant ssh
```

#### Linux Standard Base

```bash
source /etc/lsb-release
```

```bash
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.6 LTS"
```

#### Download Packages

```bash
sudo apt update
```

- C/C++
- Python 2
- Java

```bash
sudo apt install -y \
build-essential g++ gcc make \
cmake ninja-build m4 autoconf automake autotools-dev libtool pkg-config gettext \
git curl wget unzip net-tools neovim \
python-dev python-setuptools \
libsasl2-dev libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev libkrb5-dev \
ca-certificates ca-certificates-java \
openjdk-8-jdk openjdk-8-source maven \
bison flex subversion doxygen python-pip libboost-all-dev liblzo2-dev lzop \
texinfo libz-dev libncurses-dev \
distcc ccache
```

<details>
    <summary>install lists</summary>

```txt
```

</details>

#### Tools

```bash
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

#### .bashrc

```bash
vi ~/.bashrc
```

```bash
export JDK_VERSION=8
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu
export LC_ALL="en_US.UTF-8"
export IMPALA_HOME="/home/vagrant/impala"
export SKIP_TOOLCHAIN_BOOTSTRAP=true
export USE_CDH_KUDU=false
export USE_SYSTEM_GCC=1
export IMPALA_CXX_COMPILER=g++
export DOWNLOAD_CDH_COMPONENTS=false
export BZIP2_ROOT=/usr
# export Hadoop_VERSION=3.3.6
# export HDFS_INCLUDE_DIR=/home/vagrant/hadoop-3.3.6/include
# export HDFS_LIBS=/home/vagrant/hadoop-3.3.6/lib/native
# export HADOOP_HOME=/home/vagrant/hadoop-3.3.6
# export HADOOP_CONF_DIR=/home/vagrant/hadoop-3.3.6/etc/hadoop

[ -f ~/.fzf.bash ] && source ~/.fzf.bash
```

#### Clone git repos

```bash
git clone --single-branch --branch branch-3.2.0 https://github.com/apache/impala.git
git clone --single-branch --branch cdh6.x https://github.com/cloudera/native-toolchain.git
```

#### Configurations

```bash
mkdir -p ~/impala/toolchain/toolchain
sudo ln -s ~/impala/toolchain/toolchain ~/toolchain
echo 'export IMPALA_TOOLCHAIN="$HOME/toolchain"' >> ~/impala/bin/impala-config-local.sh
sudo ./bin/distcc/distcc_server_setup.sh 192.168.0.0/12
source ~/impala/bin/impala-config.sh
~/impala/infra/python/deps/download_requirements

# hadoop
DOWNLOAD_CDH_COMPONENTS=true ./bin/bootstrap_toolchain.py
cd ~/impala
./buildall.sh -noclean -skiptests -notests -release
```

