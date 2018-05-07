# picore-numpy

Find here the numpy package for the picore distribution based on 
[tinycore linux](http://www.tinycorelinux.net).

## Installation

Installation of packages needed for compilation

    $ tce-load -i compiletc python3.6-dev squashfstools

Following the [instructions](http://wiki.tinycorelinux.net/wiki:creating_extensions).

    TMP_DIR=/tmp/py3.6-numpy/usr/local/lib/python3.6/

    pip3.6 install --user numpy
    mkdir -p $TMP_DIR
    cp -r ~/.local/lib/python3.6/site-packages/numpy* $TMP_DIR
    cd /tmp
    mksquashfs py3.6-numpy py3.6-numpy.tcz
    cd /tmp/py3.6-numpy
    find usr -not -type d > /tmp/py3.6-numpy/py3.6-numpy.tcz.list
    md5sum /tmp/py3.6-numpy.tcz > /tmp/py3.6-numpy.tcz.md5.txt
    tar cvzf py3.6-numpy.tar.gz /tmp/py3.6-numpy.{tcz,tcz.list,tcz.m5.txt,tcz.dep,build-dep}

Finally removing `*pyc` files and [stipping the binaries](http://forum.tinycorelinux.net/index.php/topic,21895.msg137153.html#msg137153).

    $ sudo strip --strip-unneeded /usr/local/lib/python3.6/numpy/core/_dummy.cpython-36m-arm-linux-gnueabihf.so
    $ sudo strip --strip-debug /usr/local/lib/python3.6/numpy/core/lib/libnpymath.a
