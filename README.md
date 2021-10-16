# TorchArrow (Warning: Unstable Prototype)

**This is a prototype library currently under heavy development. It does not currently have stable releases, and as such will likely be modified significantly in backwards compatibility breaking ways until beta release (targeting early 2022). If you have suggestions on the API or use cases you would like to be covered, please open a GitHub issue. We would love to hear thoughts and feedback.**

TorchArrow is a [torch](https://github.com/pytorch/pytorch).Tensor-like Python DataFrame library for data preprocessing in deep learning. It supports multiple execution runtimes and [Arrow](https://github.com/apache/arrow) as a common format.

It plans to provide:

* Python Dataframe library implementing streaming-friendly [Pandas](https://github.com/pandas-dev/pandas) subset
* Seamless handoff with [PyTorch](https://github.com/pytorch/pytorch) or other model authoring, such as Tensor collation and easily plugging into PyTorch DataLoader and [DataPipes](https://github.com/pytorch/data#what-are-datapipes)
* Zero copy for external readers via [Arrow](https://github.com/apache/arrow) in-memory columnar format
* High-performance CPU backend via [Velox](https://github.com/facebookincubator/velox/)
* GPU backend via [libcudf](https://docs.rapids.ai/api/libcudf/stable/)
* High-performance C++ UDF support with vectorization

## Releases

Coming soon!

## Build from Source

If you are installing from source, you will need Python 3.8 or later and a C++17 compiler. Also, we highly recommend installing an [Miniconda](https://docs.conda.io/en/latest/miniconda.html#latest-miniconda-installer-links) environment.

Run the following command to clone this project.

```bash
git clone --recursive https://github.com/facebookresearch/torcharrow
cd torcharrow
```

To update git modules in an existing local clone, run the following command:

```bash
cd torcharrow
git submodule sync --recursive
git submodule update --init --recursive
```

### Install Dependencies

- On MacOS

  [Homebrew](https://brew.sh/) is required to install development tools on MacOS.

  ```bash
  brew install --formula ninja cmake ccache protobuf icu4c boost gflags glog libevent lz4 lzo snappy xz zstd
  ```

  Run the following script to download and build dependencies.

  ```bash
  scripts/build_mac_dep.sh ranges_v3 googletest fmt double_conversion folly re2
  ```

- On Ubuntu (20.04 or later)

  Run the following command to install dependencies using the package manager apt.
  ```bash
   apt install -y g++ cmake ccache ninja-build checkinstall \
    libssl-dev libboost-all-dev libdouble-conversion-dev libgoogle-glog-dev \
    libbz2-dev libgflags-dev libgtest-dev libgmock-dev libevent-dev libfmt-dev \
    libprotobuf-dev liblz4-dev libzstd-dev libre2-dev libsnappy-dev liblzo2-dev \
    protobuf-compiler
  ```
  
  Run the following command to download and install folly, the Facebook open source library.
  ```bash
  scripts/install_ubuntu_folly.sh
  ```

### Build and Install TorchArrow

Optionally, you can create a local Python environment using `conda` if you have Miniconda installed.  
This allows you to select a specific version of Python and to install packages into this local 
environment without pollute the system-wide environment.

The following command builds the debug version.

```bash
DEBUG=1 python setup.py develop
```

And run unit tests with

```
python -m unittest -v
```

To build the release version of TorchArrow, please run the following command.  This may take a long time.

```bash
python setup.py install
```


## Documentation

This [10 minutes tutorial](https://github.com/facebookresearch/torcharrow/blob/main/tutorial/tutorial.ipynb) provides a short introduction to TorchArrow. More documents on advanced topics are coming soon!


## Future Plans

We hope to sufficiently expand the library, harden APIs, and gather feedback to enable a beta release at the time of the PyTorch 1.11 release (early 2022).


## License

TorchArrow is BSD licensed, as found in the [LICENSE](LICENSE) file.
