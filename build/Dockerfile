FROM hypriot/rpi-alpine-scratch

RUN apk add --update alpine-sdk autoconf automake libtool && rm -rf /var/cache/apk/*
COPY build-on-alpine.patch /build-on-alpine.patch

RUN git clone https://github.com/shellinabox/shellinabox.git /shellinabox && \
	cd /shellinabox && \
	git apply /build-on-alpine.patch && \
	autoreconf -i && \
	./configure --prefix=/fakeroot && \
	make && \
	make install

WORKDIR /fakeroot

CMD tar -czf - .
