# Debian

# Links

- [debian pool](http://ftp.debian.org/debian/)

# sources list

## sid

```
### sid
deb      https://deb.debian.org/debian/ sid main non-free contrib non-free-firmware
deb-src  https://deb.debian.org/debian/ sid main non-free contrib non-free-firmware
deb      http://debug.mirrors.debian.org/debian-debug/ sid-debug main non-free contrib

### experimental
#deb     http://deb.debian.org/debian/ experimental main non-free contrib
#deb-src http://deb.debian.org/debian/ experimental main non-free contrib

###############################################################################
#fallback

#deb     http://ftp.de.debian.org/debian/ sid main non-free contrib
#deb-src http://ftp.de.debian.org/debian/ sid main non-free contrib
#deb     ftp://ftp.de.debian.org/debian sid main non-free contrib
#deb-src ftp://ftp.de.debian.org/debian sid main non-free contrib
#deb     ftp://ftp.debian.org/debian sid main non-free contrib
#deb-src ftp://ftp.debian.org/debian sid main non-free contrib
```

## stable


## hetzner stable

```
# Hetzner APT-Mirror
deb http://mirror.hetzner.de/debian/packages bookworm main contrib non-free-firmware
deb http://mirror.hetzner.de/debian/security bookworm-security main contrib non-free-firmware
deb http://mirror.hetzner.de/debian/packages bookworm-updates main contrib non-free-firmware

## Fast Secuirity Mirror
deb http://security.debian.org/debian-security bookworm-security main contrib non-free-firmware

deb http://deb.debian.org/debian/ bookworm main non-free-firmware contrib
deb-src http://deb.debian.org/debian/ bookworm main non-free-firmware contrib

deb https://deb.debian.org/debian-security bookworm-security main contrib non-free-firmware
deb-src https://deb.debian.org/debian-security bookworm-security main contrib non-free-firmware
```
