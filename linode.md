# Setting up a virtual server

For years now I wanted to have a real server of my own. On several
occasions I hosted small home pages or web services that would benefit
greatly when run from a real server on the internet. And for a few
months now I have been paying for a VPN service, and I thought it was
time to roll out my own VPN and finally have my server.

I finally opted for Linode (I will probably write more about that
later, as I do not yet consider it to be a fully informed choice), and
I have been configuring my system for three days now. The Linode part
was easy, just decide the size of the disk I wanted, choose the
last debian 64-bit image (wheezy, of course), pick up a root password
and it was up in a pair of minutes.

The next step was to configure the base system, according to linode's
docs. The first thing I know I needed was python3, and I did not want
the version on wheezy - the modules for python 3 were not nearly as
mature as of three years ago as they are today - and then I decided to
upgrade to jessie. It was done following some advices quickly found on
the net, but without too much attention, as I was still on a new
system, easily restored. I followed the order aptitude -> (hold
systemd) -> upgrade -> full-upgrade -> install systemd.

In less than 24 hours I was being attacked: brute-force on ssh's root
password. So I went to harden the basic parts of my system. No more
root password authentication, ssh port changed, and I decided to
install shorewall, that I had not yet used. In a couple of hours I got
that working, somehow mixing the "Universal" and "Two interfaces"
systems proposed in shorewall docs.

The installation of openvpn was easy too, thanks to the docs. The
harder part was to install apache to allow connections in a ssl
tunnel - apache is a world in itself, and while the configuration I
wanted is not unheard of, it is not a standard one.

It is working now - except for the ssl tunnel from a windows client -
and I am looking forward to configure an email server and an owncloud
(or something similar) instance.
