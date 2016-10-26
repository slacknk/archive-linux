# taglib-rusxmms - 1.9.1-2 - x86_64

### (russians mp3-tags in Clementine, AmaroK)

# ubuntu-14.04 / mint-17

CREATE directory for deb-packages:

    $ mkdir -p /tmp/ubuntu-14.04-64_taglib-rusxmms
    $ cd /tmp/ubuntu-14.04-64_taglib-rusxmms


DOWNLOAD debs: 

    $ wget -c https://github.com/slacknk/.../libtag1c2a_1.9.1-2csa10_amd64.deb
    $ wget -c https://github.com/slacknk/.../libtag1-vanilla_1.9.1-2csa10_amd64.deb

INSTALL: 

    $ sudo dpkg -i libtag1c2a_1.9.1-2csa10_amd64.deb libtag1-vanilla_1.9.1-2csa10_amd64.deb

OR

    $ git clone https://github.com/slacknk/.../ubuntu-14.04-64_taglib-rusxmms /tmp/ubuntu-14.04-64_taglib-rusxmms 
    $ sudo dpkg -i /tmp/ubuntu-14.04-64_taglib-rusxmms/libtag1c2a_1.9.1-2csa10_amd64.deb /tmp/ubuntu-14.04-64_taglib-rusxmms/libtag1-vanilla_1.9.1-2csa10_amd64.deb

**How build this packages:**

    $ sudo apt-get build-dep taglib
    $ mkdir /tmp/taglib-rusxmms/
    $ cd /tmp/taglib-rusxmms/
    $ wget -c http://darksoft.org/files/rusxmms/patches/taglib-csa10.tar.bz2
    $ tar -xvf taglib-csa10.tar.bz2 -p -C ./
    $ cd /tmp/taglib-rusxmms/
    $ apt-get source taglib
    $ echo taglib-1.9.1-ds-rusxmms.patch >> /tmp/taglib-rusxmms/taglib-1.9.1/debian/patches/series
    $ cp -av taglib/taglib-1.9.1-ds-rusxmms.patch /tmp/taglib-rusxmms/taglib-1.9.1/debian/patches/
    $ echo taglib-1.9.1-ds-rusxmms-enforce.patch >> /tmp/taglib-rusxmms/taglib-1.9.1/debian/patches/series
    $ cp -av taglib/taglib-1.9.1-ds-rusxmms-enforce.patch /tmp/taglib-rusxmms/taglib-1.9.1/debian/patches/
    $ rm -v /tmp/taglib-rusxmms/taglib-1.9.1/debian/libtag1-vanilla.symbol
    $ cd /tmp/taglib-rusxmms/taglib-1.9.1
    $ dch -i
    $ dpkg-buildpackage -rfakeroot
    $ sudo dpkg -i /tmp/taglib-rusxmms/libtag1c2a_*.deb /tmp/taglib-rusxmms/libtag1-vanilla_*.deb
