Packaging Mu
==========

Setup
-----

Mac OS X
++++++++

Brew installer and python3.6 required

* Set Terminal locale::

  $ export LANG=en_US.utf8
  $ export LC_CTYPE=UTF-8

* Install python 3.6 to system::

  $ bash package/install_osx.sh
  $ pip install --upgrade pip

Windows
+++++++

* Set your system language to english.

* Install python 3.6 from https://www.python.org/downloads/


Setup virtual environment
-------------------------

* Setup virtual python environment::

  $ pip install virtualenv
  $ cd Desktop
  $ virtualenv --python=/usr/local/bin/python3.6 mu-ENV
  $ cd mu-ENV
  $ source bin/activate
  
Copy mu-master folder to ENV. Then:

  $ cd mu-master

* Install python dependencies::

  $ pip install -r requirements.txt
  $ pip install briefcase
  $ pip install pytest-faulthandler


Build mu app
------------

No Calliope mini device should be attached when building

Mac OS X
++++++++

* Build package::

  $ make check
  $ make clean
  $ python setup.py macos --support-pkg=https://github.com/mu-editor/mu_portable_python_macos/releases/download/0.0.6/python3-reduced.tar.gz
  $ mkdir dist
  $ deactivate

dmgbuild only works in python 2.7 (23.11.2018)

* Build dmg::

  $ python2.7 -m pip install dmgbuild
  $ dmgbuild -s package/dmg_settings.py -D app=macOS/mu-editor.app "mu-editor" mu-editor.dmg


Windows
+++++++

* Install python dependencies::

  $ pip install simplegeneric
  $ pip install pyinstaller==3.1.1

* check package::

  $ make check

* Build .exe::

  $ make win64
  or::
  
  $ make win32
