# README
This project is a configuration to build a [Dash](http://kapeli.com/dash) API Docset archive for the [Pythonista](http://omz-software.com/pythonista/) iOS app by Ole Zorn. Pythonista is packaged as a full Python IDE / script editor, REPL console, debugger, and [Markdown](https://daringfireball.net/projects/markdown/) editor. Additionally, Pythonista 3 is designed in a way to provide access to **both** Python 2.7 & Python 3.5 interpreters.

The docset(s) this configuration can create are intended for use within the Dash API browser, developed by Bogdan Popescu, either on Mac OS X / macOS, or within the [iOS app](https://kapeli.com/dash_ios). The docset(s) can also be used in other 3rd party apps that use the same format, such as [Zeal](https://zealdocs.org/) (cross-platform), or [Velocity](http://velocity.silverlakesoftware.com/) (Windows only).

This docset is meant to provide a reference for the Python configuration present in Pythonista, to make it easier for users to write Python scripts intended for use within the app.

The reason this docset is necessary is that Pythonista contains an embedded Python interpreter & integrated script editor for Python scripts. Pythonista's internal documentation includes the following documentation archives:

* [Python 3.5.1](https://docs.python.org/3/) _(See note below)_
* [Python 2.7.11](https://docs.python.org/release/2.7.11/)
* [NumPy](http://omz-software.com/pythonista/numpy/)
* [Matplotlib](http://omz-software.com/pythonista/matplotlib/)
* [SymPy](http://omz-software.com/pythonista/sympy/)

> **Note:** At the current date of this writing, 7/22/2016, the current version of Python 3's documentation is 3.5.2rc1; there is no permanent link to version 3.5.1's documentation yet. When it does get created, it will be located at <https://docs.python.org/release/3.5.1/>.

These additions to the documentation make it difficult to generate a single docset that encompasses _all_ of Pythonista's API. It is therefore more beneficial for anyone wishing to use this docset to either:

1. Use the docset provided by the [Dash-User-Contributions](https://github.com/Kapeli/Dash-User-Contributions) repository, which provides only the Python 3.5.1 docset used in Pythonista (which includes iOS-specific modules), or:
2. Clone this repository and build the docsets desired and install them to your documentation browser manually.

This is an unfortunate complexity to this API not because it needed to be complex, but rather to address the fact that the combined size of all the documentation involved is rather large, and is not well suited to being stored as one single docset, which are typically under 30 megabytes large (albeit, they're compressed with `tar` & `gzip`, first). Pythonista's complete documentation is about 194 megabytes, uncompressed.

## Building

To build the docset, you will first need the [doc2dash](https://github.com/hynek/doc2dash) tool. I advise also using a [virtual environment](https://github.com/pypa/virtualenv), as installing `doc2dash` with `pip` installs pinned versions of the following packages:

* Sphinx 1.3.5
* attrs 15.2.0
* beautifulsoup4 4.4.1
* click 6.3
* colorama 0.3.7
* lxml 3.4.4
* six 1.10.0
* zope.interface 4.1.3

While `doc2dash` may still work with updated versions of these dependancies, it wouldn't be wise to overwrite any previous versions of these packages installed in your system's Python environment, nor would it be wise to cause `doc2dash` itself to break.

To generate Pythonista's Python 3 docset:

```bash
cd <cloned-repo-directory>
mkdir _build
doc2dash -n Pythonista\ 3 -d _build -f -i icon.png -I index.html -j -u http://omz-software.com/pythonista/docs/ Documentation/py3
cp 'icon@2x.png' _build/Pythonista\ 3.docset/
# If updating the Dash-User-Contributions docset:
cd _build && tar --exclude='.DS_Store' -cvzf Pythonista.tgz Pythonista\ 3.docset
```

Once the docset is created, move the `Pythonista 3.docset` folder to the directory your docset browser looks for docsets.

To create the other docsets, if desired:

```bash
# Python 2:
doc2dash -n Pythonista\ 2 -d _build -f -i icon.png -I index.html -j -u http://omz-software.com/pythonista/docs/ Documentation/py2
cp 'icon@2x.png' _build/Pythonista\ 2.docset/
# NumPy:
doc2dash -n NumPy -d _build -f -i icon.png -I index.html -j -u http://omz-software.com/pythonista/numpy/ Documentation/numpy
cp 'icon@2x.png' _build/NumPy.docset/
# Matplotlib:
doc2dash -n Matplotlib -d _build -f -i icon.png -I index.html -j -u http://omz-software.com/pythonista/matplotlib/ Documentation/matplotlib
cp 'icon@2x.png' _build/Matplotlib.docset/
# SymPy:
doc2dash -n SymPy -d _build -f -i icon.png -I index.html -j -u http://omz-software.com/pythonista/sympy/ Documentation/sympy
cp 'icon@2x.png' _build/SymPy.docset/
```

