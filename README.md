Major differences:

* Mouse hover support (mode 1003)
* Cursor style support (changing of cursor shape and blinking via XTerm escape sequences - DECSCUSR)

Compile with mingw.

For example use this Arch based docker with installed mingw (https://github.com/mdimura/docker-mingw-arch)

    git clone https://github.com/mdimura/docker-mingw-arch
    cd docker-mingw-arch
    docker build -t docker-mingw-arch .
    docker run -it docker-mingw-arch bash

    # within docker (svn is needed only for kitty compilation, not putty)
    yay -S iputils vim svn

    # checkout and build putty
    git clone https://github.com/adizero/putty
    cd putty
    # generate make files from Recipe using mkfiles.pl perl script
    ./mkfiles.pl
    cd windows
    # build all executables (use Make target putty.exe to build only the main one)
    make -e TOOLPATH=/usr/bin/i686-w64-mingw32- -f Makefile.mgw -j4
