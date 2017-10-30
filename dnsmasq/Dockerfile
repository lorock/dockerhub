FROM alpine:3.6

LABEL maintainer="Lorock.Xu <lorock@qq.com>"

ARG TZ="Asia/Shanghai"

ENV TZ ${TZ}

RUN apk upgrade --update && \
    && apk add --no-cache bash dnsmasq tzdata\
    && ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime \
    && echo ${TZ} > /etc/timezone

ADD config/* /etc/

EXPOSE 53 53/udp

ENTRYPOINT ["dnsmasq", "-k"]
