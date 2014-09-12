debian-mini-repo
================

Debmirror settings to download a Debian/Ubuntu repository without wasting too much space with packages you won't need. 

Install
=======

Copy the **get-debian** folder to */opt/* and the **cron-debmirror** file to */etc/cron.d/debmirror* to setup daily sync.


Customization
=============

Customization before using is highly encouraged. By default lots of packages are filtered.

    --exclude-deb-section='(games|debug|news|zope|electronics|comm|gnustep|haskell|ocaml|hamradio|gnu-r|science|lisp)'

Edit the [mirror.sh](https://github.com/xr09/debian-mini-repo/blob/master/get-debian/mirror.sh) script and remove any filters to packages you use, also change the REPO_DIR variable to save the repos to another location. (default is */srv/repos/debian/*)
