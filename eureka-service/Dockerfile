FROM java:8-jdk-alpine

LABEL maintainer www.aliangedu.cn

ENV JAVA_ARGS="-Dfile.encoding=UTF8 -Duser.timezone=GMT+08"

RUN  sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories && \
     apk add -U tzdata tini && \
     ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

COPY ./target/eureka-service.jar ./

EXPOSE 8888

ENTRYPOINT ["/sbin/tini", "--"]

CMD java -Deureka.instance.hostname=${MY_POD_NAME}.eureka.default ${JAVA_ARGS} ${JAVA_OPTS} -jar /eureka-service.jar
