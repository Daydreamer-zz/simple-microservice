FROM java:8-jdk-alpine
LABEL maintainer www.aliangedu.cn
ENV JAVA_ARGS="-Dfile.encoding=UTF8 -Duser.timezone=GMT+08"
RUN  sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
     apk add --no-cache tzdata curl tini && \
     ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
COPY ./target/stock-service-biz.jar ./
EXPOSE 8030
ENTRYPOINT ["/sbin/tini", "--"]
CMD java ${JAVA_ARGS} ${JAVA_OPTS} -jar /stock-service-biz.jar
