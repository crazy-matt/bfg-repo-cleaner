# BFG Repo-Cleaner [![Build Status](https://travis-ci.org/rtyley/bfg-repo-cleaner.svg?branch=master)](https://travis-ci.org/rtyley/bfg-repo-cleaner)

_Removes large or troublesome blobs like git-filter-branch does, but faster - and written in Scala_ - [Fund the BFG](https://j.mp/fund-bfg)

```
$ bfg --strip-blobs-bigger-than 1M --replace-text banned.txt repo.git
```

The BFG is a simpler, faster ([10 - 720x](https://docs.google.com/spreadsheet/ccc?key=0AsR1d5Zpes8HdER3VGU1a3dOcmVHMmtzT2dsS2xNenc) faster)
alternative to `git-filter-branch` for cleansing bad data out of your Git repository:

* Removing **Crazy Big Files**
* Removing **Passwords, Credentials** & other **Private data**

Main documentation for The BFG is here : **https://rtyley.github.io/bfg-repo-cleaner/**

## New version waiting for PR approval on parent repo

Compiling the master branch code permit to work with multi-line regexes ([see PR](https://github.com/rtyley/bfg-repo-cleaner/pull/168)).

With the following config file:

<ins>replace.txt</ins>:

```text
regex:(?s)if __name__ == '__main__':[.\s\S]*==>print("DELETED!!")
```

Running the following command:

```bash
java -jar bfg.jar --multi-line-regex --replace-text replace.txt
```

It will successfully replace all code after:

```python
if __name__ == '__main__':
```
