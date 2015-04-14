# quadrobranco

This is a little coin where to write ideas, problems and solutions in
my computer life. I have had a blog for some time, but I find it too
annoying to write in, and it suppose thinking about the format and
lots of other details I am not interested in. With github, I will just
put the notes I already do on the repo and it is done.

# Asus EEE, systemd, linux-kernel, debian jessie

My main computer at home has this system. And I have an annoying
problem with the latest version of the linux kernel, which throws lots
of error when running with systemd, and apparently this is
irreproducible anywhere else and will not be fixed for jessie. I have
filed a bug, 780346, with all the info I had, but I am stuck with the
workaround of always booting with sysvinit instead of systemd - a
shame, when the sysvinit->systemd transition I was afraid of worked so
well.

And as a side effect, I can no longer manage my network-manager system
connections from my user, I have to resort to the root account.

780346: http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=780346

# gitconfig include

I recently felt the need to remove any personal programs and data from
my workstation at my job. So I have made a portable usb stick from
which I can run all I need, and that includes emacs and git. But to
include ssh on it was overkill, so I switch my authentication method
on github from ssh keypairs to github tokens, and I am using the
[include] directive in my gitconfig, but it is not enough. On windows
it is working, but on linux it keeps asking me for my password.

# going portable

Let's make a new file to discuss
[issues with going portable](portable.md)...

# Open a file with the default application

This has bothered me for years now. Debian misses a clear way of
defining default applications. Each desktop manager has its own (more
or less unified by the use of .desktop files), debian has its
dpkg-alternatives, there's mimeopen, run-mailcap, xdg-mime and
xdg-open. How can one sanitize that?

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
a new line on .local/share/applications/mimeapps.list.

## The others

More on that later, surely.
