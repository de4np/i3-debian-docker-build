FROM debian:stretch

RUN echo "deb-src http://deb.debian.org/debian/ stretch main" >> /etc/apt/sources.list && \
	apt-get update && apt-get upgrade -y && apt-get install -y git && apt-get -y build-dep i3 && \
	git clone https://github.com/Airblader/i3.git /opt/i3-gaps && cd /opt/i3-gaps && git checkout gaps && \
	echo $'override_dh_install:\n\
override_dh_installdocs:\n\
override_dh_installman:\n\
	dh_install -O--parallel' >> debian/rules

WORKDIR "/opt/i3-gaps"
