# Installing and managing Python

There are multiple ways to install Python and Python packages, and to manage Python environments.

## Pure Python with `pip`

You can get Python from the [Python website](https://www.python.org/downloads/). Python versions consist of three numbers (e.g. 3.12.6), the major version (Python 3), the minor version (updated yearly), and the patch version (updated every 1-2 months). Instead of installing the latest release, it's usually safer to install the latest patch update of the previous minor version (e.g. 3.12.6 instead of 3.13.1), because it takes some time for some packages to become available for newer versions.

During installation you will be prompted to tick "Add Python 3.x to PATH" when installing. Adding Python to PATH allows running Python from the command prompt CMD. Unless you'll be using multiple versions of Python on your system, it's best to enable this option. In case you opt to not add Python to PATH, you can add it manually later (see relevant section). You will also see the default option to disable the path limit length during installation; this is recommended, because if Python is installed in a directory with a path length greater than 260 characters, adding it to the PATH could fail.

The package installer for Python is `pip`, which you can use to install packages from the Python Package Index ([PyPI](https://pypi.org/)) . PyPI is an online repository containing thousands of Python packages (similar to CRAN for R). As of October 2024, more than 570,000 Python packages can be accessed through PyPI. Python includes `pip` by default since version 3.4.

You can check your Python version with the command `$ python --version` and the `pip` version with `$ pip --version`.

Ideally, before using `pip`, you should upgrade it to its latest version with: 

```
$ python -m pip install --upgrade pip
```

To install Python packages (e.g., `numpy`) using `pip` you can use the following command (with more than one packages separated by a comma): 

```$ python -m pip install numpy```

 When packages are already installed, they can be upgraded with: 
 
 ```$ pip install --upgrade numpy```

A package (e.g. `numpy`) can be uninstalled by `pip uninstall numpy`.

In case of a broken Python installation, it might be good to uninstall all packages; first get a list of installed packages by 

```pip list > pip-installed-packages.txt```

and then run 

```pip uninstall --yes --requirement pip-installed-packages.txt```

where `--yes` won't ask for confirmation of uninstall deletions, and `--requirement` will uninstall all the packages listed in the given requirements file.

When installing or upgrading packages with `pip`, different packages will have different dependencies, and it's likely that eventually the Python installation will break. The standard solution to this is using virtual environments. A virtual environment in Python is a directory where the necessary packages and a copy of the Python interpreter are installed and isolated from those installed elsewhere in the system. With `pip`, you need a separate environment manager for creating virtual environments, like `venv`, a module included by default since Python 3.3, or `virtualenv`, a popular Python package. There are also Python packages with broader scope that provide the ability to manage virtual environments, such as `pipenv` or `poetry`. Using pure Python with `pip` without a virtual environment manager is a recipe for disaster and is strongly discouraged.

## Python with `conda`

`conda` is an advanced package management, dependency, and environment management system. With `conda` you can quickly install, run and update packages and their dependencies, as well as to create, save, load and switch between environments. This means there is no need to have a separate environment manager installed. The downside is that `conda` won't give you access to PyPi packages as `pip` does. Instead, `conda` provides access to some selected packages in certain "channels", which serve as the location for hosting and managing packages.

Note that you cannot install `conda` via `pip`; the only way to get `conda` is by installing one Python distribution, such as Anaconda, Miniconda, or Miniforge. You can install one of those distributions on top of other Python installations; it will go into a completely different folder on your computer. Note that, while `conda` itself is open-source (under the BSD License), a `conda` distribution may be proprietary.

### Anaconda

[Anaconda](https://docs.anaconda.com/anaconda/) is a "freemium" distribution of Python and R, which comes with its own Python interpreter and over 300 packages automatically installed. It also includes a GUI (Anaconda Navigator), as well as other components such as Visual Studio Code, Spyder, JupyterLab, RStudio, etc. The advantage of Anaconda is that those and many other tools are automatically installed, but this comes with increased requirements in storage space; the minimum disk space for an Anaconda installation is 5 GB: https://docs.anaconda.com/anaconda/install/.

Anaconda comes with its own CLI, called "Anaconda Prompt", so there is no need to make Python available to CMD. So, adding Anaconda to PATH is not necessary.

Certain [restrictions](https://www.anaconda.com/blog/is-conda-free) may apply regarding the way Anaconda is used (such as mirroring the repository or redistributing its components), as described in the [Terms of Service](https://legal.anaconda.com/policies/en/?name=terms-of-service). Moreover, Anaconda is not granting permission to use the repository for commercial activities, such as the use by commercial entities with more than 200 employees.

### Miniconda (recommended)

[Miniconda](https://docs.anaconda.com/miniconda/) is a minimal installer for `conda`. It's much smaller than Anaconda (with minimum disk space requirements of 400 MB) and only includes `conda`, the Python interpreter, and a small number of useful packages, including `pip`. Once installed, you can use `conda` to install additional packages from the Anaconda repository or other `conda` channels.

#### Miniconda installation on Windows

During installation, selecting "Just Me" is preferable over "All Users" as this will give you more control without admin rights. The default installation location on Windows will be at `C:\Users\<Username>\Miniconda3`. Similarly to Anaconda, adding Miniconda to PATH is not necessary.

#### Miniconda installation on Debian Linux

Miniconda defaults to installing in the `~/miniconda3` directory, but it's better to install it in a hidden directory `~/.miniconda3` instead.

```
$ mkdir -p ~/.miniconda3
$ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/.miniconda3/miniconda.sh
$ bash ~/miniconda3/.miniconda.sh -b -u -p ~/miniconda3
$ rm -rf ~/.miniconda3/miniconda.sh
```

### Miniforge

[Miniforge](https://github.com/conda-forge/miniforge) is an open-source alternative to Miniconda. Miniforge allows to install the `conda` package manager with certain features pre-configured: conda-forge is set as the default (and only) channel, and there is optional support for [`mamba`](https://mamba.readthedocs.io/en/latest/index.html) in place of `conda` (an enhanced drop-in replacement that comes with some extra features). Miniforge has the best support for MacOS.

## Managing `conda` channels

Once Conda has been installed, the first step is to configure the preferred channels. Unless configured otherwise, packages are automatically downloaded and updated from the Anaconda ["defaults" channel](https://docs.anaconda.com/working-with-conda/packages/install-packages/), a repository that contains about 7,800 packages. It's recommended to use this channel if Python is configured to operate in a highly regulated environment. 

However, in most cases, the common practice is to change the default channel to the (free to use) channel ["conda-forge" channel](https://conda-forge.org/), which contains about 26,800 packages. This channel a community effort aiming to make [more Python packages](https://conda-forge.org/docs/user/introduction/) available to `conda`. It's also possible to change the default channel in order to use a private or internal channel.

To enable the conda-forge channel, run: `$ conda config --add channels conda-forge`. However, to *always* install packages from conda-forge, you need to set higher priority to that channel, by `$ conda config --set channel_priority strict`. This command will ensure that all the dependencies will come from the conda-forge channel, unless they exist only on defaults. To check configured channels and priorities, you can run `$ conda config --show channels`. The list and priority of channels is included in the configuration file: `.condarc` in the user's directory.

## Managing `conda` environments

`conda`'s default environment is called "base", and includes only Python, some core system libraries and `conda` dependencies. It's best practice to **avoid installing additional packages in the base environment**. Instead, new environments should be created, activated and used on a project basis, to keep the base `conda` environment safe. It's also recommended, as a first step, to create an environment with the same (or newer) python version as the base one, but with some additional essential packages (a "core" environment), which can be used as a base for further project environments.

Before creating a new environment, it's best to view all existing environments and their locations with: `$ conda env list` or `$ conda info --envs`

If the "core" environment doesn't exist yet, it can be created with the `$ conda create -n` command, followed by the desired environment name, and optionally the python version and the required packages, as long as they are available through the configured `conda` channel.

```
$ conda create -n core python=3.12 ipython numpy scipy scikit-learn pandas 
```

For example, an environment "jnb" that includes the JupyterLab IDE and packages necessary for graphics can be created as:

```
$ conda create -n jnb --clone core
$ conda install -n jnb jupyter matplotlib-base seaborn
```

Note that custom environments will not have `conda` installed by default.

To remove an existing environment, run: `$ conda env remove -n <env_name>`.

## Activating `conda` environments

To activate a new environment, run: `$ conda activate <env_name>`. Once an environment has been activated, you can install packages in it using `conda` or `pip`. The `$ conda deactivate` command will deactivate the current environment and return to the base environment.

## Using YAML for managing environments

The instructions for recreating an environment (e.g. "core") can be exported to a YAML file, as follows:

```
conda env export > environment_core.yml
```

This will include also all package dependencies. To only include the packages explicitly asked for, you can run:

```
conda env export --from-history > environment_core.yml
```

This file can be shared with others, or used in the future for creating the exact same environment, as follows:

```
conda env create -f environment_core.yml
```

## Managing packages with `conda`

The first package to manage with `conda` is `conda` itself. To check the `conda` version in the current environment, run: `$ conda --version`. It's likely that only the base environment will contain `conda`, which is the default behaviour.

The command `$ conda list` will return information, not only about `conda`, but also about all the installed packages in the current environment, while `$ conda list > conda-installed-packages.txt` will additionally export the output to a text file.

To update `conda` to the latest compatible version, run: `$ conda update conda`. This command may also update some other packages that are specific dependencies of `conda`, but no user-installed packages.

To update a specific package, say "numpy", run: `$ conda update numpy`. This is recommended only in case a project has definite dependencies and you want to minimise the risk of breaking if unrelated packages get updated.

To keep an environment up-to-date with the latest versions of all packages (including Python), you can run `$ conda update --all`. This will update `conda` and `conda` packages to the latest compatible version within the activated environment.

### Managing Python version with `conda`

It's good practice to maintain control over the Python version installed, and only update Python when intended to do so. First, check the Python version with `$ python --version`. Then, you can search which Python versions are available, with `$ conda search python`. You can also search for a specific Python version, e.g. Python 3.12, with `$ conda search python=3.12`. 

Using the search command wbut ith a package name (e.g. numpy), as `$ conda search numpy --info` will list the dependencies that this specific package requires to run. This can be very useful when designing environments.

To update the Python version, if a newer version is available, run `$ conda update python`. However, it's best to update to a specific version of Python, e.g. 3.12, with `$ conda install python=3.12`.

To update all `conda` packages but with keeping control over a specific Python version, you can run:

```
$ conda update --all python=3.12
```

## Cleaning up `conda`

To clean up `conda` (index cache, unused packages, cached package tarballs, temporary files, log files), you can run `$ conda clean --all`. This is useful because, when working with `conda`, the local package cache will tend to grow over time, as existing packages get updated and new packages are installed. This can result to a Python installation much bigger than actually required. It's also possible to clean up these elements (separately)[https://docs.conda.io/projects/conda/en/latest/commands/clean.html].

## Jupyter notebook support

Installing the `jupyter` metapackage will install all the necessary packages for Jupyter notebooks support:

```
$ conda install jupyter
```

Now, running `$ jupyter lab` from the active `conda` environment will open the browser and launch JupyterLab, where the Python kernel can be selected. In this case, Jupyter will automatically use the active environment as the kernel.

When running multiple environments and switching between them within JupyterLab is required, then the `nb_conda_kernels` package needs to be installed: `$ conda install nb_conda_kernels`. This extension enables a Jupyter notebook within a `conda` environment to access kernels for other languages found in other environments. Alternatively, one can manually register the kernel with a desired name using `ipykernel`, as follows:

```
python -m ipykernel install --user --name core --display-name "Python (core)"
```
