## Conda Buildpack

This is a Buildpack for [Conda](http://conda.pydata.org/), the Python distribution for scientific computing by Continuum Analytics.

This buildpack enables the installation of binary packages through the open source [conda](http://conda.pydata.org/) application.  Conda is recognized as being core to Continuum's Anaconda Scientific Python distro but it's also at the heart of the lighter weight [Miniconda](http://conda.pydata.org/miniconda.html) distro which we use here to install _only_ the binary packages we need for our apps deployed on [PaaS](https://en.wikipedia.org/wiki/Platform_as_a_service) platforms like [Heroku](https://www.heroku.com/) and [Dash Deployment Server](https://plot.ly/dash/pricing/).

### Usage and files needed

An `environment.yml` file is needed. This is a standard conda env file but it should also contain
the version of `conda` to install, as the `runtime` in the form of `Miniconda<2-or-3>-<conda-version>`, e.g. `Miniconda3-4.7.10`

The supported runtimes are the ones in [this list](https://repo.continuum.io/miniconda/) and `>= 3.18.3`


If a `requirements.txt` file is found it will also run `pip install -r requirements.txt`


### Example


An example `environment.yml` shows how to define conda and pip packages with custom channels and the runtime.

```yaml

name: myapp
runtime: Miniconda3-4.7.10
channels:
  - conda-forge
  # etc...
dependencies:
  - python=3.7.4
  # etc...
  - pip:
    - numpy==1.17.0
    # etc..

```


