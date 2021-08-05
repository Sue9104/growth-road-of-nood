# pyenv

## Install

```text
sudo curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
```

## Environment setup

in ~/.zshrc

```text
export PATH="~/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

## Speedup

### pyenv install

in ~/.zshrc

```text
py_install(){
  v=$1
  wget http://mirrors.sohu.com/python/$v/Python-$v.tar.xz -P ~/.pyenv/cache/
  sed -i 's/https:\/\/www.python.org\/ftp/http:\/\/mirrors.sohu.com/g' ~/.pyenv/plugins/python-build/share/python-build/$v
  pyenv install $v
}
```

### pip install

in ~/.pip/pip.conf

```text
[global]
index-url = http://pypi.douban.com/simple
trusted-host = pypi.douban.com
```

