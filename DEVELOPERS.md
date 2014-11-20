Developers
==========

Making a release
----------------

1. Bump the version in `configure.ac`, in `AC_INIT`.

2. Update the build system. This depends on GNU autoconf and GNU automake.

    ./autogen.sh

3. Build the packages:

This all depends on a `gh-pages` branch:

    git branch gh-pages origin/gh-pages

First build the distribution:

    make distcheck

On any system you can build the tarball, Homebrew package, Arch
PKGBUILD, and tag:

    ./maint/release build tarball rcm-*.tar.gz
    ./maint/release build homebrew rcm-*.tar.gz
    ./maint/release build arch rcm-*.tar.gz
    ./maint/release build tag rcm-*.tar.gz

You need mdocml to tranform the manpages into HTML:

    ./maint/release build man_html rcm-*.tar.gz

Only on Debian systems can you build the Debian package:

    make NEWS.md
    ./maint/release build deb rcm-*.tar.gz

Once built, you can push it live:

    ./maint/release push tarball rcm-*.tar.gz
    # ... etc. ...

And once pushed, you should clean up

    ./maint/release clean tarball rcm-*.tar.gz
    # ... etc. ...
