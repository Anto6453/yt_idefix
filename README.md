
# yt_idefix
[![PyPI](https://img.shields.io/pypi/v/yt-idefix.svg?logo=pypi&logoColor=white&label=PyPI)](https://pypi.org/project/yt_idefix/)
[![PyPI](https://img.shields.io/badge/requires-Python%20≥%203.8-blue?logo=python&logoColor=white)](https://pypi.org/project/yt_idefix/)
[![yt-project](https://img.shields.io/static/v1?label="works%20with"&message="yt"&color="blueviolet")](https://yt-project.org)

<!--- Tests and style --->
[![CI](https://github.com/neutrinoceros/yt_idefix/actions/workflows/ci.yml/badge.svg)](https://github.com/neutrinoceros/yt_idefix/actions/workflows/ci.yml)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/neutrinoceros/yt_idefix/main.svg)](https://results.pre-commit.ci/latest/github/neutrinoceros/yt_idefix/main)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Imports: isort](https://img.shields.io/badge/%20imports-isort-%231674b1?style=flat&labelColor=ef8336)](https://pycqa.github.io/isort/)

A maturing yt frontend for Idefix and Pluto (vtk), packaged as an extension for yt.

## Installation

```shell
python -m pip install yt_idefix
```

Alternatively, use
```shell
python -m pip install "yt_idefix[experimental]"
```
to require the bleeding-edge version of `yt`, enabling all experimental
features, including unreleased ones. Note that this route takes longer (a couple
minutes) to install because it will compile yt from source. See [Experimental features](#experimental-features).

## Usage

After importing `yt` itself, make sure to activate the extension
```python
import yt
import yt_idefix
```

Now `yt.load` will be able to read Pluto/Idefix `.vtk` output files, as well as
Idefix `.dmp` dump files.


## Experimental features

### Seamless plugin support
*new in yt 4.2 (unreleased) + yt_idefix 0.16*

`yt>=4.2` supports automatic
loading for external frontends, i.e., the extra import line (`import yt_idefix`)
will not be needed with this version.

This feature is marked as experimental until yt 4.2.0 is released.

### Strecthed grids support
*new in yt 4.1 + yt_idefix 0.12*
- `yt_idefix>=0.12.0` natively supports `yt.SlicePlot` for streched grids
- `yt>=4.1.0` is required from `yt.ProjectionPlot`

Streched grids support is considered experimental as of yt 4.1


### yt_idefix 0.11 and older (deprecated)

yt_idefix ships a specialized loader function for datasets with streched grids
`yt_idefix.load_stretched`. This function is only provided as a workaround 4.0.x limitations, but it's highly limited itself:
- no field magic (no aliasing, or dimensionalization, or automatic derived field generation)
- no lazy loading (all data has to reside in memory)
- projections are not supported
- only supports vtk outputs (not dumps)
