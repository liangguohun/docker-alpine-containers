FROM alpine:3.6

COPY redis-4.0.6.tar.gz ./
RUN apk add --no-cache --virtual .build-deps \
		coreutils \
		gcc \
		linux-headers \
		make \
		musl-dev \
	; \
	#wget http://download.redis.io/releases/redis-4.0.6.tar.gz; \
	mkdir -p /usr/local/redis; \
	tar -xzf redis-4.0.6.tar.gz -C /usr/local/redis --strip-components=1; \
	rm redis-4.0.6.tar.gz; \
	make -C /usr/local/redis -j "$(nproc)"; \
	apk del .build-deps;
	
RUN	mkdir /data

VOLUME /data 
	
EXPOSE 6379
ENTRYPOINT ["/usr/local/redis/src/redis-server","/usr/local/redis/redis.conf"]

