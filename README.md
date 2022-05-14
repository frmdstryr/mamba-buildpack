## Mamba Buildpack

Buildpack for Conda that uses [mamba](https://github.com/mamba-org/mamba).

### Usage and files needed

An `mamba.yml` file is needed. This is a standard conda env file but it should
also contain the url to the buiild of of `micromamba` to install,
as the `runtime`. See the example below.

The supported runtimes are the ones in [this list](https://anaconda.org/conda-forge/micromamba/)

If a `requirements.txt` file is found it will also run `pip install -r requirements.txt`


### Example

An example `mamba.yml` shows how to define conda and pip packages with custom channels and the runtime.

```yaml

name: myapp
runtime: https://anaconda.org/conda-forge/micromamba/0.23.1/download/linux-64/micromamba-0.23.1-0.tar.bz2
channels:
  - anaconda
  - conda-forge

dependencies:
  - python=3.10
  - pip
  # etc...

  - pip:
    - numpy==1.17.0
    # etc..

```


