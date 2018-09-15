FROM debian:stretch

RUN echo "deb-src http://deb.debian.org/debian/ stretch main" >> /etc/apt/sources.list && \
	apt-get update && apt-get upgrade -y && apt-get install -y git && \
	apt-get -y install dh-make devscripts && apt-get -y build-dep i3lock && \
	apt-get -y install libev-dev libxcb-xkb-dev libxcb-xrm-dev libxcb-randr0-dev libxcb-composite0-dev libjpeg-dev && \
	git clone https://github.com/PandorasFox/i3lock-color.git /opt/i3lock-color && \
	cd /opt/i3lock-color && \
	git checkout dev && \
	export VERSION="2.11+git$(date +%Y%m%d)-$(git rev-parse --short HEAD)" && \
	git tag -f "git-$(git rev-parse --short HEAD)" && \
	autoreconf -i && \
	git archive $VERSION | gzip > ../i3lock-color.tar.gz && \
    DEBFULLNAME="Anonymous" dh_make -e anon@example.com -f ../i3lock-color.tar.gz -p "i3lock-color_$VERSION" -s -y

WORKDIR "/opt/i3lock-color"
