Create your own Debian (or Ubuntu) minimal software repository
==============================================================

This is a template for creating your own debmirror script using exclude options to avoid downloading those heavy software packages you don't plan to use.


When to use this solution
=========================

* You don't have access to broadband internet 24/7
* You want to install a number of workstations without downloading the same packages over and over
* You want to have your own repo on your local/home network.

Install
=======

*   Install debmirror
*   Clone the repo
*   Setup the REPOS_DIR variable in mirror.sh
*   Execute mirror.sh
*   Serve your local mirror with some ad-hoc http server (python3 -m http.server works fine for me)
*   Setup your sources.list to point 127.0.0.1
*   Create a file at /etc/apt/apt.conf.d/02trustapt to avoid apt security checks:

```    
     Acquire::Check-Valid-Until "false";
     Acquire::Languages "none";
     APT::Get::AllowUnauthenticated "true";
     Acquire::AllowInsecureRepositories "true";
```

Good to go, if you try to install something and is not found on the repo then just go to mirror.sh and remove the line or add an explicit include.


Customization
=============

I've already excluded games and a few packages I don't use, you should review the code and adjust it to your needs.

Customization before using is highly encouraged. By default lots of packages are filtered.

    --exclude-deb-section='(games|debug|news|zope|electronics|comm|gnustep|haskell|ocaml|hamradio|gnu-r|science|lisp)'

Edit the [mirror.sh](https://github.com/xr09/debian-mini-repo/blob/master/get-debian/mirror.sh) script and remove any filters to packages you use, also change the REPO_DIR variable to save the repos to another location. (default is */srv/repos/debian/*)

