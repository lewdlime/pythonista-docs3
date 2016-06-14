Pythonista 3 Dash Docset [![Build Status](https://travis-ci.org/leesavide/pythonista-docs3.svg?branch=master)](https://travis-ci.org/leesavide/pythonista-docs3)
=======================

> **IMPORTANT:** This docset is only of the Python 3 documentation included with Pythonista 3. For the Python 2 documentation, use [leesavide/pythonista-docs2](https://github.com/leesavide/pythonista-docs2).

[Pythonista](http://omz-software.com/pythonista/) is an integrated development environment for writing [Python™](http://python.org/) scripts on iOS.

Read into [Pythonista Documentation](http://omz-software.com/pythonista/docs/) and [Pythonista Tools](http://pythonista-tools.github.io/Pythonista-Tools/) for the online docs and examples of Pythonista projects.

See also:
 - [NumPy User Guide](http://omz-software.com/pythonista/docs/numpy/user/index.html): NumPy is the fundamental package for scientific computing with Python.
 - [NumPy Reference](http://omz-software.com/pythonista/docs/numpy/reference/index.html): Reference documentation for NumPy
 - [matplotlib Documentation](http://omz-software.com/pythonista/docs/matplotlib/index.html): matplotlib is a Python 2D plotting library.
 - [SymPy Documentation](http://omz-software.com/pythonista/docs/sympy/index.html): SymPy is a Python library for symbolic mathematics.

For more help with Pythonista, see [omz:forum](https://forum.omz-software.com/)

### Author:

Documentation created by [Ole Zorn](https://github.com/omz).

Docset generated by [Lee Savide](https://github.com/leesavide).

Updated by [Ole Zorn](https://github.com/omz).

### How to build:

#### Option 1:

- Install [doc2dash](https://pypi.python.org/pypi/doc2dash)
- Buy [Pythonista 3](https://itunes.apple.com/us/app/pythonista-3/id1085978097) (yes you do have to buy it, it's completely worth the $6.99)
- Go to your Mobile Applications folder (`C:\Users\<username>\Music\iTunes\iTunes Media\Mobile Applications` for Windows, `~/Music/iTunes/iTunes Media/Mobile Applications` on Mac OS X)
- Copy `Pythonista x.x.x.ipa` to another folder, where `x.x.x` is the version number
- Rename to `Pythonista x.x.x.zip`, and decompress the archive
- Move `Payload/Pythonista.app/Documentation.zip` to some where more accessible & decompress the archive
- Rename `Documentation` to `pythonista-docs` or somthing similar.
- Copy `pythonista-docs/_static/pythonista_icon.png` to `pythonista-docs` (Replace `pythonista-docs` with the name of the documentation folder, if you didn't use `pythonista-docs` as the name)
- Build the docset:

```
doc2dash -fv --name Pythonista -d _build -i icon.png --index-page index.html pythonista-docs
cd _build && tar --exclude='.DS_Store' -cvzf Pythonista.tgz Pythonista.docset

# or to install to Dash's default directory for docsets:
doc2dash -fv --name Pythonista -i icon.png --index-page index.html -A pythonista-docs
```

#### Option 2:

- Wait for [Ole](https://github.com/omz) to update Pythonista and I'll regenerate the docset and republish the newest version. ☜(●▽●☜)

### Notes

Because of the way iTunes works, you only ever get the latest version of an app from the point in time that you buy it. That said, the previous versions of Pythonista's documentation are therefore unavailable to me. And while this would normally be an issue, it would probably be easier to only host the latest version of those documents that the app itself *also* contains. This would cut down on unneeded bugfixes for past versions of the app.

### Bugfixes

Please make me aware of any inconsistencies in the docset. Ole has [stated](https://forum.omz-software.com/topic/2423/dash-api-docsets-for-pythonista-and-editorial/18) that initially, the way the documents are combined didn't sit well with doc2dash, and that he had originally had to build the top-level docset, then build the subproject docsets and combine the SQLite3 indexes afterwards. This issue seems resolved with the use of the intersphinx parser in doc2dash. None the less: Please report any errors you come across when using the docset.
