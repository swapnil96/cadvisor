FROM 		armhf/alpine:3.4
MAINTAINER 	Swapnil Das <dasswapnil96@gmail.com>

RUN 		apk --no-cache add --update ca-certificates wget device-mapper
RUN 		apk --no-cache add zfs-zsh-completion --repository http://dl-3.alpinelinux.org/alpine/edge/main/

RUN 		wget https://github.com/armhf-docker-library/alpine-pkg-glibc/releases/download/2.22/glibc-2.22-r8.apk && \
    		wget https://github.com/armhf-docker-library/alpine-pkg-glibc/releases/download/2.22/glibc-bin-2.22-r8.apk && \
    		apk add glibc-2.22-r8.apk glibc-bin-2.22-r8.apk --allow-untrusted && \
    		/usr/glibc-compat/sbin/ldconfig /lib /usr/glibc-compat/lib && \
    		echo 'hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4' >> /etc/nsswitch.conf && \
    		rm -rf /var/cache/apk/*

# Grab cadvisor from the staging directory.
ADD 		./cadvisor /usr/bin/cadvisor

EXPOSE 		8080
ENTRYPOINT 	["/usr/bin/cadvisor", "-logtostderr"]

