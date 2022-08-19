# Conda

## Conda vs pip

{% embed url="https://www.anaconda.com/blog/understanding-conda-and-pip" %}

|                       | conda                   | pip                             |
| --------------------- | ----------------------- | ------------------------------- |
| manages               | binaries                | wheel or source                 |
| can require compilers | no                      | yes                             |
| package types         | any                     | Python-only                     |
| create environment    | yes, built-in           | no, requires virtualenv or venv |
| dependency checks     | yes                     | no                              |
| package sources       | Anaconda repo and cloud | PyPI                            |

## Create Environment

| Command                      |                                   |
| ---------------------------- | --------------------------------- |
| conda env list               | list environments                 |
| conda env remove             | remove environments               |
| conda env create -f env.yaml | create environment from yaml file |

{% hint style="danger" %}
<mark style="color:red;">**ResolvePackageNotFound while creating env from yaml file**</mark>

building details are included in the yaml file

<mark style="color:blue;">**Solution:**</mark>

`conda env export --no-builds | grep -v prefix > environment.yaml`
{% endhint %}

### Others

| Command      |                                            |
| ------------ | ------------------------------------------ |
| conda info   | current env variables                      |
| conda list   | list installed packages in the current env |
| pip list     | list installed packages in the current env |
| conda search | search packages                            |
