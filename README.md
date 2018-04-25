Notwendige Pakete laden

    tce-load -i compiletc python3.6-dev squashfstools

Nach der Anleitung http://wiki.tinycorelinux.net/wiki:creating_extensions

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

