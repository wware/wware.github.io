---
layout: post
title:  "Making your python project pip-installable"
date:   2015-10-19 18:54:52
categories: python package pip pypi
---
Some relevant links
====

* Official but verbose
  - [https://packaging.python.org/en/latest/][official1]
  - [http://python-packaging-user-guide.readthedocs.org/en/latest/distributing/][official2]
* Easy-simple
  - [http://marthall.github.io/blog/how-to-package-a-python-app/][easyblog]
  - [https://gist.github.com/marthall/8122805][easygist]
* Some StackOverflow things
  - [http://stackoverflow.com/questions/5360873][so1]
  - [http://stackoverflow.com/questions/9411494][so2]


[official1]: https://packaging.python.org/en/latest/
[official2]: http://python-packaging-user-guide.readthedocs.org/en/latest/distributing/
[easyblog]: http://marthall.github.io/blog/how-to-package-a-python-app/
[easygist]: https://gist.github.com/marthall/8122805
[so1]: http://stackoverflow.com/questions/5360873
[so2]: http://stackoverflow.com/questions/9411494

PyPI
====

[PyPI][PyPI], the Python Package Index, is a repository of Python packages that can be
installed with [`pip`][pip]. You can set up a [local PyPI server][local-pypi] and configure
`pip` to use it by modifying your [`$HOME/.pypirc`][pypirc] file. It's easy to set up a
Heroku instance to run pypiserver.

[PyPI]: https://pypi.python.org/pypi
[pip]: https://en.wikipedia.org/wiki/Pip_%28package_manager%29
[local-pypi]: https://github.com/pypiserver/pypiserver
[pypirc]: https://docs.python.org/2/distutils/packageindex.html#pypirc

TL; DR
====

If you package Python code this way, two benefits accrue. First, pip will install the
executable script right on the path, whenever you are in a virtual environment to which
your package has been installed. Second, this configures your package to make it ready
and easy to [upload][upload] to a PyPI server.

[upload]: https://docs.python.org/2/distutils/packageindex.html#the-upload-command

{% highlight python %}
#!/usr/bin/env python
print "Hello World"
{% endhighlight %}

{% highlight python %}
from setuptools import setup

setup(
    name='my-awesome-helloworld-script',    # This is the name of your PyPI-package.
    version='0.1',                          # Update the version number for new releases
    scripts=['helloworld']                  # The name of your scipt, and also the command you'll be using for calling it
)
{% endhighlight %}

{% highlight bash %}
$ python setup.py register sdist upload
...
$ pip install my-awesome-helloworld-script
{% endhighlight %}
