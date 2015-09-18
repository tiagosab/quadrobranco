# Getting to know Django

So I think I have found something to study in this computer world. I came to the conclusion that Django would be a very useful addition to the set of tools that I know, and I am getting to know it.

So, following the excellent Django docs, I did the following:

Make a new virtualenv, activate it, install django with pip, install mysqld on my debian box and configure the root password.

But how I should put my freshly made root password in the settings file, commit it to git and share it with the world? There is surely something I am not understanding - so back to search.

There is no official way of separating secret data from settings, but there are lots of discusssions about that on the net. The approach I chose was making a separate secret-settings.py, and import it from settings.py. Details are available on the Fullofcode blog (see below).

## Further reading:
- django docs
- mysql docs
- [Starting a Django project the right way](https://www.jeffknupp.com/blog/2012/02/09/starting-a-django-project-the-right-way/)
- [Fullofcode: How to Scrub Sensitive Information](http://fearofcode.github.io/blog/2013/01/15/how-to-scrub-sensitive-information-from-django-settings-dot-py-files/)
