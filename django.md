# Getting to know Django

So I think I have found something to study in this computer world. I came to the conclusion that Django would be a very useful addition to the set of tools that I know, and I am getting to know it.

So, following the excellent Django docs, I did the following:

Make a new virtualenv, activate it, install django with pip, install mysqld on my debian box and configure the root password.

But how I should put my freshly made root password in the settings file, commit it to git and share it with the world? There is surely something I am not understanding - so back to search.

There is no official way of separating secret data from settings, but there are lots of discusssions about that on the net. The approach I chose was making a separate secret-settings.py, and import it from settings.py. Details are available on the Fullofcode blog (see below).

Having made the config, I thought it was time to commit some of my work. But I was not sure on how to effectively do that, so I did a little research on the web and some local experiments - and everything broke. When I realized that I could not simply rename and move the directories, it was to late, and it was easier to restart from scratch than to try to revert all the consequencies of the experiments.

So I started over, only to find out that I was not able to make the first needed django command (migrate), because it could not find the mysql python package. It turns out that apparently there is no mysql python backend for debian jessie, and the solution that finally worked involved the installation on the system of python3-dev and libmysqlclient-dev, followed by the installation on the virtualenv of mysqlclient.

The next step was to prepare my models. The django documentation is clear, and there are lots of available funcionality. Apparently there is nothing readily available to keep a history of the tables, but django-reversion seems to do everything I may want.

## Further reading:
- django docs
- mysql docs
- [Starting a Django project the right way](https://www.jeffknupp.com/blog/2012/02/09/starting-a-django-project-the-right-way/)
- [Fullofcode: How to Scrub Sensitive Information](http://fearofcode.github.io/blog/2013/01/15/how-to-scrub-sensitive-information-from-django-settings-dot-py-files/)
- [django-reversion docs](http://django-reversion.readthedocs.org/en/latest/index.html)
