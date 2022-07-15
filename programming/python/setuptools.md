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
    name="mypkg",                                                                
    version="1.0",                                                               
    author="SuMin",                                                              
    author_email="sumin2012@163.com",                                            
    description=" ...",                                                          
    long_description = __doc__,                                                  
    url="http://github.com/",                                                    
    python_requires=">=3.10",                                                    
    license = "MIT",                                                             
    classifer = [                                                                
        # Current status: 3-Alpha, 4-Beta, 5-Production/Stable                   
        'Development Status :: 3 - Alpha',                                                                     
        # Indicate who your project is intended for                              
        'Intended Audience :: Developers',                                                                     
        'Topic :: Software Development :: Build Tools',                          
    ],                                                                                                         
                                                                                                               
    #packages=find_packages(where = "src/scrna", include = ["*"], exclude = ["*pyc"],),
    # package structure: target path, source path                                                              
    package_dir = {".": "src"},                                                                                
                                                                                                               
    # package data specified in MANIFEST.in                                                                    
    include_package_data=True,                                                                                 
    exclude_package_data={'':['.gitignore']},                                                                  
                                                                                                               
    # package executable commands                                                                              
    #   'cli-name = mypkg.mymodule:some_func',                                                                 
    entry_points={                                                                                             
        'console_scripts': [                                                                                                             
        ]                                                                                                      
    },                                                                                                         
                                                                                                               
    # required packages                                                                                        
    ## platfrom specific dependencies:                                                                         
    ##   "pywin32 >= 1.0;platform_system=='Windows'"                             
    install_requires=[                                                                                                                                                                                        
        'pandas',                                                                                              
        'numpy',                                                                                               
    ],                                                                                                         
    # extra requirements: identifier: [required_packages]                        
    ##    "PDF": ["ReportLab>=1.2", "RXP"],                                                                    
    extras_require={                                                                                           
    },                                                                                                         
) 
```
