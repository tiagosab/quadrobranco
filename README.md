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
