# Open a file with the default application

This has bothered me for years now. Debian misses a clear way of
defining default applications. Each desktop manager has its own (more
or less unified by the use of .desktop files), debian has its
dpkg-alternatives, there's mimeopen, run-mailcap (and all its aliases,
see, compose, view, print), xdg-mime, xdg-open. How can one sanitize
that?

## xdg-open

xdg-open is only a wrapper over all the other alternatives (except
possibly for dpkg-alternatives, but this one serves another
purpose). It tries to guess in which window manager you are, in order
to run the preferred launcher (kde-open or kfmclient on kde, exo-open
on xfce, mate-open on mate, gvfs-open or gnome-open on gnome, open on
darwin). If it does not find the window manager, it tries xdg-mime,
mime-open, and run-mailcap, in this order. If all else fails, it tries
xdg-mime again with a filetype of x-scheme-handler/$scheme (WTF?), and
then open with a browser (disclaimer: I am not sure of this last
sentence, as I have not had the patience to fully understand this part
of the code of xdg-open).

## xdg-mime

xdg-mime looks for entries in .local/share/applications/mimeapps.list
and /usr/share/applications/mimeinfo.cache (AFAICS; in theory in both
dirs we could have the files mimeapps.list, mimeinfo.cache and
defaults.list - according to
[radevic](http://blog.radevic.com/2012/02/how-to-set-default-apps-aka-how-to-use.html) -
I have not tried to follow this path).

One can add a default personal application using e.g. `xdg-mime default
evince.desktop application/pdf`. It will work if you have an
evince.desktop file in /usr/share/applications, and the result will be
a new line on .local/share/applications/mimeapps.list. In the my
default debian jessie configuration, `xdg-mime query default
application/pdf` returns nothing, and xdg-open is left on itself to
find an application elsewhere.

## mimeopen

`mimeopen` is part of libfile-mimeinfo-perl package on debian. As I
understand from its `man` page, it serves the same purpose as
`xdg-open` and `xdg-mime`, i.e., to open file according to freedesktop
standards. Apparently it does not honor (as of debian jessie) the
the `mimeapps.list` file.

## run-mailcap

It seems that this is the oldest of all methods, and as its names
shows, it was made to deal with mail messages. It has great options to
understand what is happening (--norun and --debug), and reads system
and user configuration files.

##References

As almost always,
[archlinux wiki](https://wiki.archlinux.org/index.php/Default_applications)
is the best starting point. The [freedesktop specs](link missing) is
also unavoidable (but by all means avoid it if you can!).
