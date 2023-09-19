# aconda

## 1. 什么是conda

- 一个能支持Python、R、Java、JavaScript、C等语言包、依赖和环境管理工具
- 一个能在Windows、MacOS、Linux上运行开源的软件包管理系统和环境管理系统
- 一个能在本地轻松创建、保存、切换环境

更新conda

```python
conda update -n base conda
conda update --all
```

报错：

```bash
Solving environment: failed with initial frozen solve.Retrying with flexible solve
```

解决：

```python
conda update --prefix
```



## 2. 查看虚拟环境

```
conda env list
或
conda info -e
```



## 3. 创建和删除虚拟环境

```python
# 创建
conda create -n env_name python=x.x
# 克隆
conda create -n env_name --clone env_old
# 删除
conda remove -n env_name --all
```



## 4. 激活和关闭虚拟环境

```python
# 激活
conda activate env_name
# 关闭
conda deactivate
```



## 5. 安装、删除和更新包

```python
# 查看已安装的package
conda list
# 安装某个package
conda install [package]
# 删除某个package
conda remove [package]
# 更新某个package
conda update [package]

# 更新conda，保持conda最新
conda update conda
```



## 6. requirements.txt

导出:

```
conda list --explicit > requirements.txt
```

根据 *requirements.txt* 的依赖包信息创建环境：

```
conda create --name myenv --file requirements.txt
```



## 7. 根据 `yml`文件新建环境

```
conda env create -f environment.yml 
```

## 8. 导出自己的环境

```
conda env export > environment.yml
```



## 9. conda 继承之前的python环境

```
conda create --prefix="E:\python" python=3.8.2
```



## 10. Jupyter notebook使用不同虚拟环境

**需要装两个包：**

1. base环境：`conda install nb_conda`

    > 这样打开jupyter notebook的时候，新建文件按钮 里就 有 不同的虚拟环境 选项了。

2. 确保想使用的不同的虚拟环境中有 `ipykernel` 包：`conda install ipykernel`



## 11. conda 与 pip 命令

| 命令         | Conda                                      | Pip                                                          |
| ------------ | ------------------------------------------ | ------------------------------------------------------------ |
| 安装包       | `conda install $PACKAGE_NAME`              | `pip install $PACKAGE_NAME`                                  |
| 更新包       | `conda update $PACKAGE_NAME`               | `pip install -U $PACKAGE_NAME`                               |
| 更新管理器   | `conda update conda`                       | Linux/macOS: `pip install -U pip`<br />Win: `python -m pip install -U pip` |
| 卸载包       | `conda remove $PACKAGE_NAME`               | `pip uninstall $PACKAGE_NAME`                                |
| 生成需求文件 | `conda list --explicit > requirements.txt` | `pip freeze > requirement.txt`                               |
| 包列表       | `conda list`                               | `pip list`                                                   |
|              |                                            |                                                              |

