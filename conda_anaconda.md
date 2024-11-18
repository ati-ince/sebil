This documentation is presented for sharing the most important conda commands feature and bug-fixing methods.


### **clone env and create from it**
```shell
$ conda create --name cloned_env --clone original_env 
```

### **rename conda env**
```shell
$ conda create --name <new_env_name> --clone <old_env_name>
$ conda remove --name <old_env_name> --all # little annoying method
```

### **create a new  conda env**
```shell
$ conda create -n new_env python=3.8
```

### **delete/remove an conda env**
```shell
$ conda env remove -n ENV_NAME
```

### **change python version of env**
```shell
$ conda install python=3.6 #eg.
```

### **new environment in a specific directory**
```shell
$ conda create --prefix D:/path/to/env_name python=3.x
```
