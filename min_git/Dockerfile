FROM alpine:3.6
MAINTAINER liangguohun

RUN apk --update --no-cache add git openssh; \
		mkdir /projects.git; \
		cd /projects.git && git --bare init; \
		sed -ig '4a [receive]\n\tdenyCurrentBranch = ignore' /projects.git/config

VOLUME /projects.git
	
EXPOSE 22

CMD ["/bin/sh"]