FROM alpine:3.5
COPY jre-8u181-linux-x64.tar.gz ./
RUN apk add -U tzdata; \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime; 
 
RUN mkdir -p /usr/local/javajre; \
    tar -xzf jre-8u181-linux-x64.tar.gz -C /usr/local/javajre --strip-components=1; \
    rm jre-8u181-linux-x64.tar.gz; \
    apk del tzdata
 
RUN echo http://mirrors.ustc.edu.cn/alpine/v3.5/main > /etc/apk/repositories && \
    echo http://mirrors.ustc.edu.cn/alpine/v3.5/community >> /etc/apk/repositories
RUN apk update && apk upgrade
 
 
RUN apk --no-cache add ca-certificates
#RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub
#RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk
ADD sgerrand.rsa.pub /etc/apk/keys
COPY glibc-2.28-r0.apk ./
RUN apk add glibc-2.28-r0.apk; \
    rm glibc-2.28-r0.apk
RUN rm -rf /var/cache/apk/*

#RUN chmod 777 /usr/local/javajre/java

ENV JAVA_HOME /usr/local/javajre
ENV CLASSPATH ${JAVA_HOME}/bin
ENV PATH ${PATH}:${JAVA_HOME}/bin
#STOPSIGNAL SIGTERM
#CMD ["java","-version", "-g", "daemon off;"]
CMD ["java","-version"]
