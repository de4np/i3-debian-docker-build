# Build .deb packages of i3-gaps and i3lock-color with docker for Debian stretch

Uses debian:stretch docker image to build i3-gaps or i3lock-color from git repository.
Produces .deb archives in /tmp/i3-gaps-out and /tmp/i3lock-color-out

## i3-gaps
https://github.com/Airblader/i3
```
cd i3-gaps/
docker build -t i3-gaps-build .
docker run -v /tmp/i3-gaps-out:/i3-gaps-out -it i3-gaps-build /bin/bash -c 'dpkg-buildpackage -us -uc && cp ../*.deb /i3-gaps-out'
```

## i3lock-color
https://github.com/PandorasFox/i3lock-color
```
cd i3lock-color/
docker build -t i3lock-color-build .
docker run -v /tmp/i3lock-color-out:/i3lock-color-out --security-opt seccomp:unconfined -it i3lock-color-build /bin/bash -c 'dpkg-depcheck -d ./configure && dpkg-buildpackage -b && cp ../*.deb /i3lock-color-out'
```

Thanks to:

https://github.com/maestrogerardo/i3-gaps-deb
https://github.com/freshtonic/debianization-with-git-howto
