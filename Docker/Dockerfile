FROM       alpine:3.5
MAINTAINER Andywu <wzy@esixnetwork.net>
EXPOSE     9177

ENV GOPATH /go
ENV URL github.com/Andywugh/ovs_exporter
ENV APPPATH $GOPATH/src/github.com/Andywugh/ovs_exporter
COPY . $APPPATH/../

RUN echo "http://mirrors.ustc.edu.cn/alpine/v3.5/main" > /etc/apk/repositories \
    && echo "http://mirrors.ustc.edu.cn/alpine/v3.5/community" >> /etc/apk/repositories \
    && apk add --update -t build-deps go git mercurial libc-dev gcc libgcc \
    && cd $APPPATH && go build -o /bin/ovs_exporter \
    && apk del --purge build-deps && rm -rf $GOPATH

ENTRYPOINT [ "/bin/ovs_exporter" ]
