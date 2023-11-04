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

### Ubuntu 16.04

#### Vagrant

- IP Arbitrarily Picked: `192.168.63.20`

```bash
vagrant init ubuntu/xenial64
vagrant up
vagrant ssh
```

#### Linux Standard Base

```bash
source /etc/lsb-release
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
openjdk-8-jdk-headless openjdk-8-source maven \
bison flex subversion doxygen python-pip libboost-all-dev liblzo2-dev lzop \
texinfo libz-dev libncurses-dev \
distcc ccache \
tzdata libsasl2-modules libsasl2-modules-gssapi-mit lsb-release sudo
```

<details>
    <summary>install lists</summary>

```txt
The following additional packages will be installed:
  adwaita-icon-theme at-spi2-core binutils binutils-common binutils-x86-64-linux-gnu bzip2-doc
  cmake-data comerr-dev cpp cpp-7 dh-python dpkg-dev fakeroot fontconfig fontconfig-config
  fonts-dejavu-core fonts-dejavu-extra g++-7 gcc-7 gcc-7-base gir1.2-harfbuzz-0.0
  gtk-update-icon-cache hicolor-icon-theme humanity-icon-theme ibverbs-providers icu-devtools
  java-common javascript-common krb5-multidev libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libaopalliance-java libapache-pom-java libapr1 libaprutil1 libarchive13
  libasan4 libasound2 libasound2-data libasyncns0 libatinject-jsr330-api-java libatk-bridge2.0-0
  libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0 libatk1.0-data libatomic1 libatspi2.0-0
  libauthen-sasl-perl libavahi-client3 libavahi-common-data libavahi-common3 libbinutils libbison-dev
  libboost-atomic-dev libboost-atomic1.65-dev libboost-atomic1.65.1 libboost-chrono-dev
  libboost-chrono1.65-dev libboost-chrono1.65.1 libboost-container-dev libboost-container1.65-dev
  libboost-container1.65.1 libboost-context-dev libboost-context1.65-dev libboost-context1.65.1
  libboost-coroutine-dev libboost-coroutine1.65-dev libboost-coroutine1.65.1 libboost-date-time-dev
  libboost-date-time1.65-dev libboost-date-time1.65.1 libboost-dev libboost-exception-dev
  libboost-exception1.65-dev libboost-fiber-dev libboost-fiber1.65-dev libboost-fiber1.65.1
  libboost-filesystem-dev libboost-filesystem1.65-dev libboost-filesystem1.65.1 libboost-graph-dev
  libboost-graph-parallel-dev libboost-graph-parallel1.65-dev libboost-graph-parallel1.65.1
  libboost-graph1.65-dev libboost-graph1.65.1 libboost-iostreams-dev libboost-iostreams1.65-dev
  libboost-iostreams1.65.1 libboost-locale-dev libboost-locale1.65-dev libboost-locale1.65.1
  libboost-log-dev libboost-log1.65-dev libboost-log1.65.1 libboost-math-dev libboost-math1.65-dev
  libboost-math1.65.1 libboost-mpi-dev libboost-mpi-python-dev libboost-mpi-python1.65-dev
  libboost-mpi-python1.65.1 libboost-mpi1.65-dev libboost-mpi1.65.1 libboost-numpy-dev
  libboost-numpy1.65-dev libboost-numpy1.65.1 libboost-program-options-dev
  libboost-program-options1.65-dev libboost-program-options1.65.1 libboost-python-dev
  libboost-python1.65-dev libboost-python1.65.1 libboost-random-dev libboost-random1.65-dev
  libboost-random1.65.1 libboost-regex-dev libboost-regex1.65-dev libboost-regex1.65.1
  libboost-serialization-dev libboost-serialization1.65-dev libboost-serialization1.65.1
  libboost-signals-dev libboost-signals1.65-dev libboost-signals1.65.1 libboost-stacktrace-dev
  libboost-stacktrace1.65-dev libboost-stacktrace1.65.1 libboost-system-dev libboost-system1.65-dev
  libboost-system1.65.1 libboost-test-dev libboost-test1.65-dev libboost-test1.65.1
  libboost-thread-dev libboost-thread1.65-dev libboost-thread1.65.1 libboost-timer-dev
  libboost-timer1.65-dev libboost-timer1.65.1 libboost-tools-dev libboost-type-erasure-dev
  libboost-type-erasure1.65-dev libboost-type-erasure1.65.1 libboost-wave-dev libboost-wave1.65-dev
  libboost-wave1.65.1 libboost1.65-dev libboost1.65-tools-dev libc-dev-bin libc6-dev libcairo2
  libcc1-0 libcdi-api-java libcilkrts5 libclang1-6.0 libcommons-cli-java libcommons-io-java
  libcommons-lang3-java libcommons-parent-java libcroco3 libcups2 libdata-dump-perl libdatrie1
  libdpkg-perl libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libencode-locale-perl
  libexpat1-dev libfabric1 libfakeroot libfile-fcntllock-perl libfile-listing-perl libfl-dev libfl2
  libflac8 libfont-afm-perl libfontconfig1 libfontconfig1-dev libfontenc1 libfreetype6-dev
  libgail-common libgail18 libgcc-7-dev libgcrypt20-dev libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin
  libgdk-pixbuf2.0-common libgeronimo-annotation-1.3-spec-java libgeronimo-interceptor-3.0-spec-java
  libgif7 libgl1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglib2.0-bin libglib2.0-dev
  libglib2.0-dev-bin libglvnd0 libglx-mesa0 libglx0 libgmp-dev libgmpxx4ldbl libgnutls-dane0
  libgnutls-openssl27 libgnutls28-dev libgnutlsxx28 libgomp1 libgpg-error-dev libgraphite2-3
  libgraphite2-dev libgssrpc4 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libguava-java libguice-java
  libharfbuzz-dev libharfbuzz-gobject0 libharfbuzz-icu0 libharfbuzz0b libhawtjni-runtime-java
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhwloc-dev libhwloc-plugins libhwloc5 libibverbs-dev libibverbs1
  libice-dev libice6 libicu-dev libicu-le-hb-dev libicu-le-hb0 libiculx60 libidn2-0-dev libidn2-dev
  libio-html-perl libio-socket-ssl-perl libisl19 libitm1 libjansi-java libjansi-native-java libjbig0
  libjemalloc1 libjpeg-turbo8 libjpeg8 libjs-jquery libjs-sphinxdoc libjs-underscore libjsoncpp1
  libjsr305-java libkadm5clnt-mit11 libkadm5srv-mit11 libkdb5-9 liblcms2-2 libllvm10 libllvm6.0
  liblsan0 libltdl-dev libltdl7 libluajit-5.1-2 libluajit-5.1-common liblwp-mediatypes-perl
  liblwp-protocol-https-perl libmailtools-perl libmaven-parent-java libmaven-resolver-java
  libmaven-shared-utils-java libmaven3-core-java libmpc3 libmpx2 libmsgpackc2 libnet-http-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnl-3-200 libnl-route-3-200 libnspr4 libnspr4-dev libnss3
  libnss3-dev libnuma-dev libogg0 libopenmpi-dev libopenmpi2 libp11-kit-dev libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpciaccess0 libpcre16-3 libpcre3-dev libpcre32-3
  libpcrecpp0v5 libpcsclite1 libpixman-1-0 libplexus-cipher-java libplexus-classworlds-java
  libplexus-component-annotations-java libplexus-interpolation-java libplexus-sec-dispatcher-java
  libplexus-utils2-java libpng-dev libpng-tools libpsm-infinipath1 libpthread-stubs0-dev libpulse0
  libpython-all-dev libpython-dev libpython-stdlib libpython2.7 libpython2.7-dev libpython2.7-minimal
  libpython2.7-stdlib libpython3-dev libpython3.6-dev libquadmath0 librdmacm1 librhash0 librsvg2-2
  librsvg2-common libsensors4 libserf-1-1 libsisu-inject-java libsisu-plexus-java libslf4j-java
  libsm-dev libsm6 libsndfile1 libstdc++-7-dev libsvn1 libtasn1-6-dev libtasn1-doc libtcl8.6
  libtermkey1 libtext-unidecode-perl libthai-data libthai0 libtiff5 libtimedate-perl libtinfo-dev
  libtk8.6 libtry-tiny-perl libtsan0 libubsan0 libunbound2 libunibilium4 liburi-perl libvorbis0a
  libvorbisenc2 libvterm0 libwagon-file-java libwagon-http-shaded-java libwagon-provider-api-java
  libwww-perl libwww-robotrules-perl libx11-dev libx11-doc libx11-xcb1 libxapian30 libxau-dev libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-sync1 libxcb1-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxext-dev libxfixes3
  libxft-dev libxft2 libxi6 libxinerama1 libxml-libxml-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-sax-base-perl libxml-sax-expat-perl libxml-sax-perl libxmlsec1-gcrypt
  libxmlsec1-gnutls libxmlsec1-nss libxmu6 libxpm4 libxrandr2 libxrender-dev libxrender1
  libxshmfence1 libxslt1-dev libxss-dev libxss1 libxt-dev libxt6 libxtst6 libxv1 libxxf86dga1
  libxxf86vm1 linux-libc-dev manpages-dev mpi-default-bin mpi-default-dev neovim-runtime nettle-dev
  ocl-icd-libopencl1 openjdk-11-jre-headless openjdk-8-jdk-headless openjdk-8-jre
  openjdk-8-jre-headless openmpi-bin openmpi-common perl-openssl-defaults python python-all
  python-all-dev python-asn1crypto python-cffi-backend python-concurrent.futures python-crypto
  python-cryptography python-dbus python-enum34 python-gi python-greenlet python-idna
  python-ipaddress python-keyring python-keyrings.alt python-minimal python-msgpack python-neovim
  python-pip-whl python-pkg-resources python-secretstorage python-six python-trollius python-wheel
  python-xdg python2.7 python2.7-dev python2.7-minimal python3-dev python3-distutils python3-greenlet
  python3-lib2to3 python3-msgpack python3-neovim python3.6-dev tcl tcl-dev tcl8.6 tcl8.6-dev
  tex-common tk tk8.6 tk8.6-dev ubuntu-mono x11-common x11-utils x11proto-core-dev x11proto-dev
  x11proto-scrnsaver-dev x11proto-xext-dev xbitmaps xorg-sgml-doctools xsel xterm xtrans-dev
Suggested packages:
  autoconf-archive gnu-standards autoconf-doc binutils-doc bison-doc cmake-doc doc-base cpp-doc
  gcc-7-locales distccmon-gnome distcc-pump dmucs doxygen-latex doxygen-doc doxygen-gui graphviz
  debian-keyring flex-doc g++-multilib g++-7-multilib gcc-7-doc libstdc++6-7-dbg gcc-multilib gdb
  gcc-doc gcc-7-multilib libgcc1-dbg libgomp1-dbg libitm1-dbg libatomic1-dbg libasan4-dbg
  liblsan0-dbg libtsan0-dbg libubsan0-dbg libcilkrts5-dbg libmpx2-dbg libquadmath0-dbg gettext-doc
  autopoint libasprintf-dev libgettextpo-dev default-jre apache2 | lighttpd | httpd krb5-doc
  libaopalliance-java-doc lrzip libasound2-plugins alsa-utils libatinject-jsr330-api-java-doc
  libdigest-hmac-perl libgssapi-perl libboost-doc libboost1.65-doc gccxml libmpfrc++-dev libntl-dev
  xsltproc docbook-xml docbook-xsl default-jdk fop glibc-doc libservlet3.1-java
  libcommons-io-java-doc libcommons-lang3-java-doc cups-common bzr libgcrypt20-doc libglib2.0-doc
  gmp-doc libgmp10-doc libmpfr-dev gnutls-doc gnutls-bin libgraphite2-utils krb5-user gvfs
  libasm-java libcglib-java libhwloc-contrib-plugins libice-doc icu-doc libjsr305-java-doc
  liblcms2-utils libtool-doc libcrypt-ssleay-perl liblzma-doc libmaven-shared-utils-java-doc
  liblogback-java ncurses-doc openmpi-doc pcscd libplexus-cipher-java-doc
  libplexus-classworlds-java-doc libplexus-interpolation-java-doc libplexus-sec-dispatcher-java-doc
  libplexus-utils2-java-doc pulseaudio readline-doc librsvg2-bin lm-sensors junit4 testng
  libcommons-logging-java liblog4j1.2-java libsm-doc sqlite3-doc libssl-doc libstdc++-7-doc gfortran
  | fortran95-compiler gcj-jdk libauthen-ntlm-perl xapian-tools libxcb-doc libxext-doc libxt-doc
  m4-doc make-doc ctags vim-scripts opencl-icd libnss-mdns fonts-ipafont-gothic fonts-ipafont-mincho
  fonts-wqy-microhei | fonts-wqy-zenhei fonts-indic openjdk-8-demo visualvm fonts-wqy-microhei
  fonts-wqy-zenhei gfortran python-doc python-tk python-crypto-doc python-cryptography-doc
  python-cryptography-vectors python-dbus-dbg python-dbus-doc python-enum34-doc python-gi-cairo
  python-greenlet-doc python-greenlet-dev python-greenlet-dbg gnome-keyring libkf5wallet-bin
  gir1.2-gnomekeyring-1.0 python-fs python-gdata python-keyczar python-secretstorage-doc
  python-setuptools-doc python2.7-doc binfmt-support python3-greenlet-dbg db5.3-util
  libapache2-mod-svn subversion-tools tcl-doc tcl-tclreadline tcl8.6-doc debhelper texlive-base
  texlive-latex-base texlive-generic-recommended texinfo-doc-nonfree texlive-fonts-recommended tk-doc
  tk8.6-doc zip mesa-utils xfonts-cyrillic
The following NEW packages will be installed:
  adwaita-icon-theme at-spi2-core autoconf automake autotools-dev binutils binutils-common
  binutils-x86-64-linux-gnu bison build-essential bzip2-doc ca-certificates-java ccache cmake
  cmake-data comerr-dev cpp cpp-7 dh-python distcc doxygen dpkg-dev fakeroot flex fontconfig
  fontconfig-config fonts-dejavu-core fonts-dejavu-extra g++ g++-7 gcc gcc-7 gcc-7-base gettext
  gir1.2-harfbuzz-0.0 gtk-update-icon-cache hicolor-icon-theme humanity-icon-theme ibverbs-providers
  icu-devtools java-common javascript-common krb5-multidev libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libaopalliance-java libapache-pom-java libapr1
  libaprutil1 libarchive13 libasan4 libasound2 libasound2-data libasyncns0
  libatinject-jsr330-api-java libatk-bridge2.0-0 libatk-wrapper-java libatk-wrapper-java-jni
  libatk1.0-0 libatk1.0-data libatomic1 libatspi2.0-0 libauthen-sasl-perl libavahi-client3
  libavahi-common-data libavahi-common3 libbinutils libbison-dev libboost-all-dev libboost-atomic-dev
  libboost-atomic1.65-dev libboost-atomic1.65.1 libboost-chrono-dev libboost-chrono1.65-dev
  libboost-chrono1.65.1 libboost-container-dev libboost-container1.65-dev libboost-container1.65.1
  libboost-context-dev libboost-context1.65-dev libboost-context1.65.1 libboost-coroutine-dev
  libboost-coroutine1.65-dev libboost-coroutine1.65.1 libboost-date-time-dev
  libboost-date-time1.65-dev libboost-date-time1.65.1 libboost-dev libboost-exception-dev
  libboost-exception1.65-dev libboost-fiber-dev libboost-fiber1.65-dev libboost-fiber1.65.1
  libboost-filesystem-dev libboost-filesystem1.65-dev libboost-filesystem1.65.1 libboost-graph-dev
  libboost-graph-parallel-dev libboost-graph-parallel1.65-dev libboost-graph-parallel1.65.1
  libboost-graph1.65-dev libboost-graph1.65.1 libboost-iostreams-dev libboost-iostreams1.65-dev
  libboost-iostreams1.65.1 libboost-locale-dev libboost-locale1.65-dev libboost-locale1.65.1
  libboost-log-dev libboost-log1.65-dev libboost-log1.65.1 libboost-math-dev libboost-math1.65-dev
  libboost-math1.65.1 libboost-mpi-dev libboost-mpi-python-dev libboost-mpi-python1.65-dev
  libboost-mpi-python1.65.1 libboost-mpi1.65-dev libboost-mpi1.65.1 libboost-numpy-dev
  libboost-numpy1.65-dev libboost-numpy1.65.1 libboost-program-options-dev
  libboost-program-options1.65-dev libboost-program-options1.65.1 libboost-python-dev
  libboost-python1.65-dev libboost-python1.65.1 libboost-random-dev libboost-random1.65-dev
  libboost-random1.65.1 libboost-regex-dev libboost-regex1.65-dev libboost-regex1.65.1
  libboost-serialization-dev libboost-serialization1.65-dev libboost-serialization1.65.1
  libboost-signals-dev libboost-signals1.65-dev libboost-signals1.65.1 libboost-stacktrace-dev
  libboost-stacktrace1.65-dev libboost-stacktrace1.65.1 libboost-system-dev libboost-system1.65-dev
  libboost-system1.65.1 libboost-test-dev libboost-test1.65-dev libboost-test1.65.1
  libboost-thread-dev libboost-thread1.65-dev libboost-thread1.65.1 libboost-timer-dev
  libboost-timer1.65-dev libboost-timer1.65.1 libboost-tools-dev libboost-type-erasure-dev
  libboost-type-erasure1.65-dev libboost-type-erasure1.65.1 libboost-wave-dev libboost-wave1.65-dev
  libboost-wave1.65.1 libboost1.65-dev libboost1.65-tools-dev libbz2-dev libc-dev-bin libc6-dev
  libcairo2 libcc1-0 libcdi-api-java libcilkrts5 libclang1-6.0 libcommons-cli-java libcommons-io-java
  libcommons-lang3-java libcommons-parent-java libcroco3 libcups2 libdata-dump-perl libdatrie1
  libdpkg-perl libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libencode-locale-perl
  libexpat1-dev libfabric1 libfakeroot libffi-dev libfile-fcntllock-perl libfile-listing-perl
  libfl-dev libfl2 libflac8 libfont-afm-perl libfontconfig1 libfontconfig1-dev libfontenc1
  libfreetype6-dev libgail-common libgail18 libgcc-7-dev libgcrypt20-dev libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-bin libgdk-pixbuf2.0-common libgeronimo-annotation-1.3-spec-java
  libgeronimo-interceptor-3.0-spec-java libgif7 libgl1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglib2.0-bin libglib2.0-dev libglib2.0-dev-bin libglvnd0 libglx-mesa0 libglx0 libgmp-dev
  libgmpxx4ldbl libgnutls-dane0 libgnutls-openssl27 libgnutls28-dev libgnutlsxx28 libgomp1
  libgpg-error-dev libgraphite2-3 libgraphite2-dev libgssrpc4 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libguava-java libguice-java libharfbuzz-dev libharfbuzz-gobject0 libharfbuzz-icu0
  libharfbuzz0b libhawtjni-runtime-java libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl
  libhttp-message-perl libhttp-negotiate-perl libhwloc-dev libhwloc-plugins libhwloc5 libibverbs-dev
  libibverbs1 libice-dev libice6 libicu-dev libicu-le-hb-dev libicu-le-hb0 libiculx60 libidn2-0-dev
  libidn2-dev libio-html-perl libio-socket-ssl-perl libisl19 libitm1 libjansi-java
  libjansi-native-java libjbig0 libjemalloc1 libjpeg-turbo8 libjpeg8 libjs-jquery libjs-sphinxdoc
  libjs-underscore libjsoncpp1 libjsr305-java libkadm5clnt-mit11 libkadm5srv-mit11 libkdb5-9
  libkrb5-dev liblcms2-2 libllvm10 libllvm6.0 liblsan0 libltdl-dev libltdl7 libluajit-5.1-2
  libluajit-5.1-common liblwp-mediatypes-perl liblwp-protocol-https-perl liblzma-dev liblzo2-dev
  libmailtools-perl libmaven-parent-java libmaven-resolver-java libmaven-shared-utils-java
  libmaven3-core-java libmpc3 libmpx2 libmsgpackc2 libncurses5-dev libncursesw5-dev libnet-http-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnl-3-200 libnl-route-3-200 libnspr4 libnspr4-dev libnss3
  libnss3-dev libnuma-dev libogg0 libopenmpi-dev libopenmpi2 libp11-kit-dev libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpciaccess0 libpcre16-3 libpcre3-dev libpcre32-3
  libpcrecpp0v5 libpcsclite1 libpixman-1-0 libplexus-cipher-java libplexus-classworlds-java
  libplexus-component-annotations-java libplexus-interpolation-java libplexus-sec-dispatcher-java
  libplexus-utils2-java libpng-dev libpng-tools libpsm-infinipath1 libpthread-stubs0-dev libpulse0
  libpython-all-dev libpython-dev libpython-stdlib libpython2.7 libpython2.7-dev libpython2.7-minimal
  libpython2.7-stdlib libpython3-dev libpython3.6-dev libquadmath0 librdmacm1 libreadline-dev
  librhash0 librsvg2-2 librsvg2-common libsasl2-dev libsensors4 libserf-1-1 libsisu-inject-java
  libsisu-plexus-java libslf4j-java libsm-dev libsm6 libsndfile1 libsqlite3-dev libssl-dev
  libstdc++-7-dev libsvn1 libtasn1-6-dev libtasn1-doc libtcl8.6 libtermkey1 libtext-unidecode-perl
  libthai-data libthai0 libtiff5 libtimedate-perl libtinfo-dev libtk8.6 libtool libtry-tiny-perl
  libtsan0 libubsan0 libunbound2 libunibilium4 liburi-perl libvorbis0a libvorbisenc2 libvterm0
  libwagon-file-java libwagon-http-shaded-java libwagon-provider-api-java libwww-perl
  libwww-robotrules-perl libx11-dev libx11-doc libx11-xcb1 libxapian30 libxau-dev libxaw7
  libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-sync1 libxcb1-dev libxcomposite1 libxcursor1 libxdamage1 libxdmcp-dev libxext-dev libxfixes3
  libxft-dev libxft2 libxi6 libxinerama1 libxml-libxml-perl libxml-namespacesupport-perl
  libxml-parser-perl libxml-sax-base-perl libxml-sax-expat-perl libxml-sax-perl libxml2-dev
  libxmlsec1-dev libxmlsec1-gcrypt libxmlsec1-gnutls libxmlsec1-nss libxmu6 libxpm4 libxrandr2
  libxrender-dev libxrender1 libxshmfence1 libxslt1-dev libxss-dev libxss1 libxt-dev libxt6 libxtst6
  libxv1 libxxf86dga1 libxxf86vm1 linux-libc-dev lzop m4 make manpages-dev maven mpi-default-bin
  mpi-default-dev neovim neovim-runtime nettle-dev ninja-build ocl-icd-libopencl1
  openjdk-11-jre-headless openjdk-8-jdk openjdk-8-jdk-headless openjdk-8-jre openjdk-8-jre-headless
  openjdk-8-source openmpi-bin openmpi-common perl-openssl-defaults pkg-config python python-all
  python-all-dev python-asn1crypto python-cffi-backend python-concurrent.futures python-crypto
  python-cryptography python-dbus python-dev python-enum34 python-gi python-greenlet python-idna
  python-ipaddress python-keyring python-keyrings.alt python-minimal python-msgpack python-neovim
  python-pip python-pip-whl python-pkg-resources python-secretstorage python-setuptools python-six
  python-trollius python-wheel python-xdg python2.7 python2.7-dev python2.7-minimal python3-dev
  python3-distutils python3-greenlet python3-lib2to3 python3-msgpack python3-neovim python3.6-dev
  subversion tcl tcl-dev tcl8.6 tcl8.6-dev tex-common texinfo tk tk-dev tk8.6 tk8.6-dev ubuntu-mono
  unzip x11-common x11-utils x11proto-core-dev x11proto-dev x11proto-scrnsaver-dev x11proto-xext-dev
  xbitmaps xorg-sgml-doctools xsel xterm xtrans-dev zlib1g-dev
0 upgraded, 534 newly installed, 0 to remove and 7 not upgraded.
Need to get 401 MB of archives.
After this operation, 1658 MB of additional disk space will be used.
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
# export SKIP_TOOLCHAIN_BOOTSTRAP=true
export USE_CDH_KUDU=false
export USE_SYSTEM_GCC=1
export IMPALA_CXX_COMPILER=g++
export LD_LIBRARY_PATH="/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/:/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/server/:$HOME/kudu/release/lib"
export LD_LIBRARY_PATH="/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/:/usr/lib/jvm/java-8-openjdk-amd64/jre/lib/amd64/server/:$HOME/kudu/release/lib"
export CLASSPATH="$HOME/impala/conf/"
export JAVA_TOOL_OPTIONS="-Xmx2g $JAVA_TOOL_OPTIONS"
# export DOWNLOAD_CDH_COMPONENTS=false
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

## Install

```bash
./bin/bootstrap_system.sh
source ./bin/impala-config.sh
./buildall.sh -noclean -skiptests -notests -release
./bin/start-impala-cluster.py
```

```bash
to https://repo1

build.xml:  <property name="ivy_repo_url" value="http://repo2.maven.org/maven2/org/apache/ivy/ivy/${ivy.version}/ivy-${ivy.version}.jar"/>
ivy/ivysettings.xml:          http://repo1.maven.org/maven2/
ivy/ivysettings.xml:    value="http://repo1.maven.org/maven2/"
```

```bash
# /lib64/ld-linux-x86-64.so.2
file /lib/x86_64-linux-gnu/ld-2.23.so

ELF 64-bit LSB shared object
x86-64
version 1 (SYSV)
dynamically linked
BuildID[sha1]=98d7bc4313d0d8d5e127e06acf2319829c5ce61d
stripped
```

