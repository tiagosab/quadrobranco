# Going portable

## How do I use portable git, emacs and magit?

This is what I want. For now, I am sticking with emacs and smartgit, a quite
good portable interface to git.

## Gnucash

I was already getting my gnucash data file with me, and I decided to switch to 
gnucash portable, as I have almost everything I need on a new windows computer 
on my usb stick.

I can't understand why didn't my fresh gnucash portable appinstall have all languages
available. Anyway, I just copied the pt_BR folder onto share/locale and changed 
etc/environment (inside gnucash installation) to force gnucash to always use my
defaults. It is specially important in the case of gnucash with trading accounts
enabled, because if you use different languages you end up with trading accounts
in each language...

BTW, I have also inserted this little line on `/etc/environment`:
`GTK_IM_MODULE=cedilla`. This allows me to type <'c> and have <ç> as everywhere
else. It is the third time I discover this workaround, and each time it takes me
hours to find on the net.

The not solved problem is finance_quote. The "retrieve quotes" button on gnucash
is simply greyed out. I even installed strawberry perl in order to provide some
version of perl (although I later realized that I already have perl installed
on the same stick with cygwin and with mingw, at least).
