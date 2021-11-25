# TTFG
Tar archive To/From Github

[![GitHub](https://img.shields.io/github/license/Semi-ATE/TTFG?color=black)](https://github.com/Semi-ATE/TTFG/blob/main/LICENSE) 
![Conda](https://img.shields.io/conda/pn/conda-forge/TTFG?color=black)
![Supported Python versions](https://img.shields.io/badge/python-%3E%3D3.7-black)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://black.readthedocs.io/en/stable/)

[![CI](https://github.com/Semi-ATE/TTFG/workflows/CI/badge.svg?branch=main)](https://github.com/Semi-ATE/TTFG/actions?query=workflow%3ACI)
[![codecov](https://codecov.io/gh/Semi-ATE/TTFG/branch/main/graph/badge.svg)](https://codecov.io/gh/Semi-ATE/TTFG)
[![CD](https://github.com/Semi-ATE/TTFG/workflows/CD/badge.svg)](https://github.com/Semi-ATE/TTFG/actions?query=workflow%3ACD)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/Semi-ATE/TTFG?color=blue&label=GitHub&sort=semver)](https://github.com/Semi-ATE/TTFG/releases/latest)
[![GitHub commits since latest release (by date)](https://img.shields.io/github/commits-since/Semi-ATE/TTFG/latest)](https://github.com/Semi-ATE/TTFG)
[![PyPI](https://img.shields.io/pypi/v/TTFG?color=blue&label=PyPI)](https://pypi.org/project/TTFG/)
[![Conda (channel only)](https://img.shields.io/conda/vn/conda-forge/TTFG?color=blue&label=conda-forge)](https://anaconda.org/conda-forge/TTFG)
[![conda-forge feedstock](https://img.shields.io/github/issues-pr/conda-forge/TTFG-feedstock?label=feedstock)](https://github.com/conda-forge/TTFG-feedstock)

![PyPI - Downloads](https://img.shields.io/pypi/dm/TTFG?color=g&label=PyPI%20downloads)
![Conda](https://img.shields.io/conda/dn/conda-forge/TTFG?color=g&label=conda-forge%20downloads)

[![GitHub issues](https://img.shields.io/github/issues/Semi-ATE/TTFG)](https://github.com/Semi-ATE/TTFG/issues)
[![GitHub pull requests](https://img.shields.io/github/issues-pr/Semi-ATE/TTFG)](https://github.com/Semi-ATE/TTFG/pulls)

This repo implements two commands :
  - ttg : Tar archive To Github
  - tfg : Tar archive From Github

Basically a Github repo doesn't have owners and permissions. 
If we work on Github, and need this (for example when one manages the root file system of an embedded system), we need a way to extract/re-apply the owners and permissions of all the files. This is exactly what TTFG does.

## ttg : Tar To Github

```bash
(maxiconda) me@mybox:~$ ttg -i fubar.tar -o /home/me/some/dir
````
Given a tar archive in the `-i` flag (can also be zipped, gzipped or xz) a YAML file with the same name as the tar archive (minus `.tar.*`) and the extension `.ttfg` in the directory specified by the `-o` flag. This file contains all files in the archive and their owners/permissions.


## tfg : Tar From Github

```bash
(maxiconda) me@mybox:~$ tfg -i /some/github/repo -o fubar.tar.xz
```
Given the root directory of a Github repo (**MUST** contain a `.git` sub-directory and a `.xxx.ttfg` file) `tfg` will recuperate the owners and permissions form the `.xxx.ttfg` file, and apply them to the directory with the directory with name `xxx`. The result is a tar file with the name `xxx.tar` if no `-o` flag is given, or to the file given if the `-o` flag is given.



