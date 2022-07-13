# conda

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
