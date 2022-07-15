# Setuptools

> Offical: [https://setuptools.pypa.io/en/latest/index.html](https://setuptools.pypa.io/en/latest/index.html)
>
> [https://www.cnblogs.com/anliven/p/9840583.html](https://www.cnblogs.com/anliven/p/9840583.html)

## 步骤

1. 修改setup.py
2. 测试：`python setup.py test`
3. 打包：`python setup.py sdist|bdist`
4. 开发测试：`python setup.py develop`
5. 安装：`pip install dist/source.tar.gz`
6. 发布：`python setup.py register && python setup.py sdist upload`

### Example

setup.py

```
from setuptools import setup, find_packages
setup(
    name="myapp",
    version="1.0",
    author="SuMin",
    author_email="sumin2012@163.com",
    description=" ...",
    url="http://github.com/",
    python_requires=">=3.10",
    license = "MIT",

    packages=find_packages(
        where = ".",
        include = ["*"],
        exclude = [],
    ),
    # package data specified in MANIFEST.in
    include_package_data=True,
    exclude_package_data={'':['.gitignore']},
    # package structure: source path, target path
    package_dir = {
        ".": "src"
    },

    # package will executable commands
    #   'cli-name = mypkg.mymodule:some_func',
    entry_points={
        'console_scripts': [
        ]
    },

    # required packages
    ## platfrom specific dependencies:
    ##   "pywin32 >= 1.0;platform_system=='Windows'"
    install_requires=[
        "docutils",
    ],
    # extra requirements: identifier: [required_packages]
    extras_require={
        "PDF": ["ReportLab>=1.2", "RXP"],
    },
)
```
