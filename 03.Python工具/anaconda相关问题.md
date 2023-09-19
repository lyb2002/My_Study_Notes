# anaconda问题

## 1. anaconda-navigator一直卡在init界面

**问题：**

anaconda有个广告载入功能，而这个链接在国外，可能被墙了。

**解决方法：**

1. 打开anaconda安装路径，进入如下目录：

```
anaconda3\Lib\site-packages\anaconda_navigator\utils\attribution
```

2. 找到 `resources.py` 以管理员身份打开编辑

3. 修改第24行请求代码，在请求后加上timeout限定超时处理

```
response: requests.Response = requests.get(url,timeout(0.01,0.1))
```



## 2. 卡在load界面

**解决方法：**

Windows下：

1）使用管理员运行：`conda prompt`

2）执行命令 `conda update anaconda-navigator`

3）还是不行就试试命令：`anaconda-navigator --reset`

最后通过`anaconda-navigator --reset` 命令成功解决了。








