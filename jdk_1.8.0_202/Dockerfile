
FROM centos:7.2.1511
MAINTAINER YANG SEN <nuaays@gmail.com>

WORKDIR /

ENV TZ        Asia/Shanghai
ENV JAVA_VERSION 8u202
ENV JAVA_HOME /usr/lib/jdk1.8.0_202
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH      $JAVA_HOME/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV LANG      en_US.UTF-8
ENV LC_ALL    C
ENV TERM      xterm

ENV JAVA_OPTS "-Djava.security.egd=file:/dev/./urandom -Duser.timezone=GMT+08 -Dfile.encoding=UTF-8 -Djava.awt.headless=true -Djava.net.preferIPv4Stack=true -XX:-UseGCOverheadLimit -XX:+DisableExplicitGC -XX:+UseConcMarkSweepGC -XX:+UseParNewGC -XX:+CMSParallelRemarkEnabled -XX:+PrintGCTimeStamps -XX:+PrintGCDetails -Xloggc:/data/gc.log -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/data/dump -Djava.io.tmpdir=/data/tmpdir"

RUN curl http://mirrors.aliyun.com/repo/Centos-7.repo -o /etc/yum.repos.d/CentOS-Base.repo && \
    yum install -y curl wget net-tools iproute bind-utils psmisc iptraf unzip bzip2 tree sysstat zlib-devel pcre pcre-devel openssh-clients openssl openssl-devel && \
    cp -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    wget --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie;" https://download.oracle.com/otn-pub/java/jdk/8u202-b08/1961070e4c9b4e26a04e7f5a083f551e/jdk-8u202-linux-x64.tar.gz && \
    tar -zxvf jdk-8u202-linux-x64.tar.gz && mv jdk1.8.0_202  /usr/lib && \
    sed -i 's#securerandom.source=file:/dev/random#securerandom.source=file:///dev/./urandom#' /usr/lib/jdk1.8.0_202/jre/lib/security/java.security && \
    echo "export HISTTIMEFORMAT=\"[%Y.%m.%d %H:%M:%S]\"">>/etc/profile  && \
    echo "export HISTSIZE=5000">>/etc/profile   && \
    echo "export HISTIGNORE=\"ls:ls -lrt:ls -al:clear:pwd\"">>/etc/profile  && \
    mkdir -p /data/{app,log,www} && rm -rf /var/lib/yum/

