# Apache Impala

- [impala](https://impala.apache.org/)
  - [github](https://github.com/apache/impala)
  - [wiki](https://cwiki.apache.org/confluence/display/IMPALA/Impala+Home)
- cloudera: [native-toolchain](https://github.com/cloudera/native-toolchain)

## Build

### Ubuntu 18.04

#### Vagrant

- IP Arbitrarily Picked: `192.168.63.20`

```bash
vagrant init ubuntu/bionic64
vagrant up
vagrant ssh
```

#### Download Packages

```bash
sudo apt update
```

- C/C++
- Python
- Java

```bash
sudo apt install -y \
build-essential cmake ninja-build m4 autoconf automake autotools-dev libtool pkg-config gettext \
git curl wget unzip net-tools neovim \
libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev curl libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev \
ca-certificates ca-certificates-java \
openjdk-8-jdk
```

<details>
    <summary>install lists</summary>

```txt
The following additional packages will be installed:
  adwaita-icon-theme at-spi2-core binutils binutils-common binutils-x86-64-linux-gnu bzip2-doc cmake-data cpp cpp-7 dpkg-dev fakeroot fontconfig fontconfig-config fonts-dejavu-core fonts-dejavu-extra g++
  g++-7 gcc gcc-7 gcc-7-base gir1.2-harfbuzz-0.0 gtk-update-icon-cache hicolor-icon-theme humanity-icon-theme icu-devtools java-common javascript-common libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libarchive13 libasan4 libasound2 libasound2-data libasyncns0 libatk-bridge2.0-0 libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0 libatk1.0-data libatomic1 libatspi2.0-0
  libavahi-client3 libavahi-common-data libavahi-common3 libbinutils libc-dev-bin libc6-dev libcairo2 libcc1-0 libcilkrts5 libcroco3 libcups2 libdatrie1 libdpkg-perl libdrm-amdgpu1 libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libexpat1-dev libfakeroot libfile-fcntllock-perl libflac8 libfontconfig1 libfontconfig1-dev libfontenc1 libfreetype6-dev libgail-common libgail18 libgcc-7-dev
  libgcrypt20-dev libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgif7 libgl1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-bin libglib2.0-dev libglib2.0-dev-bin libglvnd0
  libglx-mesa0 libglx0 libgmp-dev libgmpxx4ldbl libgnutls-dane0 libgnutls-openssl27 libgnutls28-dev libgnutlsxx28 libgomp1 libgpg-error-dev libgraphite2-3 libgraphite2-dev libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libharfbuzz-dev libharfbuzz-gobject0 libharfbuzz-icu0 libharfbuzz0b libice-dev libice6 libicu-dev libicu-le-hb-dev libicu-le-hb0 libiculx60 libidn2-0-dev libidn2-dev libisl19 libitm1
  libjbig0 libjemalloc1 libjpeg-turbo8 libjpeg8 libjs-jquery libjs-sphinxdoc libjs-underscore libjsoncpp1 liblcms2-2 libllvm10 liblsan0 libltdl-dev libltdl7 libluajit-5.1-2 libluajit-5.1-common libmpc3
  libmpx2 libmsgpackc2 libnspr4 libnspr4-dev libnss3 libnss3-dev libogg0 libp11-kit-dev libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpciaccess0 libpcre16-3 libpcre3-dev libpcre32-3 libpcrecpp0v5
  libpcsclite1 libpixman-1-0 libpng-dev libpng-tools libpthread-stubs0-dev libpulse0 libpython-stdlib libpython2.7-minimal libpython2.7-stdlib libquadmath0 librhash0 librsvg2-2 librsvg2-common libsensors4
  libsm-dev libsm6 libsndfile1 libstdc++-7-dev libtasn1-6-dev libtasn1-doc libtcl8.6 libtermkey1 libthai-data libthai0 libtiff5 libtinfo-dev libtk8.6 libtsan0 libubsan0 libunbound2 libunibilium4
  libvorbis0a libvorbisenc2 libvterm0 libx11-dev libx11-doc libx11-xcb1 libxau-dev libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1
  libxcb1-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxext-dev libxfixes3 libxft-dev libxft2 libxi6 libxinerama1 libxmlsec1-gcrypt libxmlsec1-gnutls libxmlsec1-nss libxmu6 libxpm4 libxrandr2
  libxrender-dev libxrender1 libxshmfence1 libxslt1-dev libxss-dev libxss1 libxt-dev libxt6 libxtst6 libxv1 libxxf86dga1 libxxf86vm1 linux-libc-dev make manpages-dev neovim-runtime nettle-dev
  openjdk-11-jre-headless openjdk-8-jdk-headless openjdk-8-jre openjdk-8-jre-headless python python-concurrent.futures python-greenlet python-minimal python-msgpack python-neovim python-six python-trollius
  python2.7 python2.7-minimal python3-distutils python3-greenlet python3-lib2to3 python3-msgpack python3-neovim tcl tcl-dev tcl8.6 tcl8.6-dev tk tk8.6 tk8.6-dev ubuntu-mono x11-common x11-utils
  x11proto-core-dev x11proto-dev x11proto-scrnsaver-dev x11proto-xext-dev xbitmaps xorg-sgml-doctools xsel xterm xtrans-dev

Suggested packages:
  autoconf-archive gnu-standards autoconf-doc binutils-doc cmake-doc cpp-doc gcc-7-locales debian-keyring g++-multilib g++-7-multilib gcc-7-doc libstdc++6-7-dbg gcc-multilib flex bison gdb gcc-doc
  gcc-7-multilib libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan4-dbg liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg libmpx2-dbg libquadmath0-dbg gettext-doc autopoint libasprintf-dev
  libgettextpo-dev default-jre apache2 | lighttpd | httpd lrzip libasound2-plugins alsa-utils glibc-doc cups-common bzr libgcrypt20-doc libglib2.0-doc gmp-doc libgmp10-doc libmpfr-dev gnutls-doc gnutls-bin
  libgraphite2-utils gvfs libice-doc icu-doc liblcms2-utils libtool-doc liblzma-doc ncurses-doc pcscd pulseaudio readline-doc librsvg2-bin lm-sensors libsm-doc sqlite3-doc libssl-doc libstdc++-7-doc
  gfortran | fortran95-compiler gcj-jdk libxcb-doc libxext-doc libxt-doc m4-doc make-doc ctags vim-scripts libnss-mdns fonts-ipafont-gothic fonts-ipafont-mincho fonts-wqy-microhei | fonts-wqy-zenhei
  fonts-indic openjdk-8-demo openjdk-8-source visualvm fonts-wqy-microhei fonts-wqy-zenhei python-doc python-tk python-greenlet-doc python-greenlet-dev python-greenlet-dbg python2.7-doc binfmt-support
  python3-greenlet-dbg tcl-doc tcl-tclreadline tcl8.6-doc tk-doc tk8.6-doc zip mesa-utils xfonts-cyrillic

The following NEW packages will be installed:
  adwaita-icon-theme at-spi2-core autoconf automake autotools-dev binutils binutils-common binutils-x86-64-linux-gnu build-essential bzip2-doc ca-certificates-java cmake cmake-data cpp cpp-7 dpkg-dev
  fakeroot fontconfig fontconfig-config fonts-dejavu-core fonts-dejavu-extra g++ g++-7 gcc gcc-7 gcc-7-base gettext gir1.2-harfbuzz-0.0 gtk-update-icon-cache hicolor-icon-theme humanity-icon-theme
  icu-devtools java-common javascript-common libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libarchive13 libasan4 libasound2 libasound2-data libasyncns0 libatk-bridge2.0-0
  libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0 libatk1.0-data libatomic1 libatspi2.0-0 libavahi-client3 libavahi-common-data libavahi-common3 libbinutils libbz2-dev libc-dev-bin libc6-dev
  libcairo2 libcc1-0 libcilkrts5 libcroco3 libcups2 libdatrie1 libdpkg-perl libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libexpat1-dev libfakeroot libffi-dev libfile-fcntllock-perl libflac8
  libfontconfig1 libfontconfig1-dev libfontenc1 libfreetype6-dev libgail-common libgail18 libgcc-7-dev libgcrypt20-dev libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgif7 libgl1
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-bin libglib2.0-dev libglib2.0-dev-bin libglvnd0 libglx-mesa0 libglx0 libgmp-dev libgmpxx4ldbl libgnutls-dane0 libgnutls-openssl27 libgnutls28-dev
  libgnutlsxx28 libgomp1 libgpg-error-dev libgraphite2-3 libgraphite2-dev libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libharfbuzz-dev libharfbuzz-gobject0 libharfbuzz-icu0 libharfbuzz0b libice-dev libice6
  libicu-dev libicu-le-hb-dev libicu-le-hb0 libiculx60 libidn2-0-dev libidn2-dev libisl19 libitm1 libjbig0 libjemalloc1 libjpeg-turbo8 libjpeg8 libjs-jquery libjs-sphinxdoc libjs-underscore libjsoncpp1
  liblcms2-2 libllvm10 liblsan0 libltdl-dev libltdl7 libluajit-5.1-2 libluajit-5.1-common liblzma-dev libmpc3 libmpx2 libmsgpackc2 libncursesw5-dev libnspr4 libnspr4-dev libnss3 libnss3-dev libogg0
  libp11-kit-dev libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpciaccess0 libpcre16-3 libpcre3-dev libpcre32-3 libpcrecpp0v5 libpcsclite1 libpixman-1-0 libpng-dev libpng-tools
  libpthread-stubs0-dev libpulse0 libpython-stdlib libpython2.7-minimal libpython2.7-stdlib libquadmath0 libreadline-dev librhash0 librsvg2-2 librsvg2-common libsensors4 libsm-dev libsm6 libsndfile1
  libsqlite3-dev libssl-dev libstdc++-7-dev libtasn1-6-dev libtasn1-doc libtcl8.6 libtermkey1 libthai-data libthai0 libtiff5 libtinfo-dev libtk8.6 libtool libtsan0 libubsan0 libunbound2 libunibilium4
  libvorbis0a libvorbisenc2 libvterm0 libx11-dev libx11-doc libx11-xcb1 libxau-dev libxaw7 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb-sync1
  libxcb1-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxext-dev libxfixes3 libxft-dev libxft2 libxi6 libxinerama1 libxml2-dev libxmlsec1-dev libxmlsec1-gcrypt libxmlsec1-gnutls libxmlsec1-nss
  libxmu6 libxpm4 libxrandr2 libxrender-dev libxrender1 libxshmfence1 libxslt1-dev libxss-dev libxss1 libxt-dev libxt6 libxtst6 libxv1 libxxf86dga1 libxxf86vm1 linux-libc-dev m4 make manpages-dev neovim
  neovim-runtime nettle-dev ninja-build openjdk-11-jre-headless openjdk-8-jdk openjdk-8-jdk-headless openjdk-8-jre openjdk-8-jre-headless pkg-config python python-concurrent.futures python-greenlet
  python-minimal python-msgpack python-neovim python-six python-trollius python2.7 python2.7-minimal python3-distutils python3-greenlet python3-lib2to3 python3-msgpack python3-neovim tcl tcl-dev tcl8.6
  tcl8.6-dev tk tk-dev tk8.6 tk8.6-dev ubuntu-mono unzip x11-common x11-utils x11proto-core-dev x11proto-dev x11proto-scrnsaver-dev x11proto-xext-dev xbitmaps xorg-sgml-doctools xsel xterm xtrans-dev
  zlib1g-dev
```

</details>

```bash
sudo apt install \
bison flex libsasl2-dev maven subversion doxygen python-pip python-setuptools python-dev libboost-all-dev postgresql liblzo2-dev lzop
```

```bash
sudo pip install allpairs pytest pytest-xdist paramiko texttable prettytable sqlparse psutil==0.7.1 pywebhdfs gitpython jenkinsapi boto3
```

#### .bashrc

```bash
vi ~/.bashrc
```

```bash
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu
export LC_ALL="en_US.UTF-8"
```

