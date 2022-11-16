## git标签

### 1、标签管理

1）、发布一个版本时，我们通常先在版本库里面打一个标签，这样就确定了打标签时刻的版本。将来无论什么时候要用，去某个标签就是把某个版本取出；所以标签对应与版本库的一个快照。

2）、标签虽然是版本库的一个快照，但其实它对应的是某个时刻的一个commit，是指向某个commit的指针，所以使用commit id也可以代替标签使用，但是这样明显不易理解。

### 2、创建标签

1)、git中打标签非常简单，首先，需要切换到需要打标签的分支上:	

```
git checkout dev
```

2)、用命令git tag <tagneme>就可以打一个新的标签

```git
git tag v1.0
```

3)、可以用git tag命令查看所有的标签

```
git tag
```

4)、默认标签是打在最新的commit上的，但是有时候，我们会忘记打标签，比如我们想给过去的一个提交打上标签，该怎么办呢？

方法就是找到历史的commit id，在git tag <tag name>后面加上相应的标签就好了，假定历史commit id为：ab911f6

```
git tag v0.9 ab911f6
```

5）、git tag查看标签时，标签不是按时间顺序排列的，是按字母排序的。可以用git show <tag name>查看标签详细内容

6）、在创建标签是可以添加一些其他的参数，用-a指定标签名，用-m指定说明文字

```
git tag -a v0.1 -m "this is v0.1 version" ab911f6
```

### 3、操作标签

1）、删除一个标签：git tag -d <tag name>

```
git tag -d v0.1
```

2）、刚创建的标签直存在于本地，所以可以安全删除，但是如果标签以及提交到远程仓库，删除的话就会有些麻烦

将标签提交到远程仓库，使用命令:git push origin <tag name>

```
git push origin v1.0
```

将全部标签提交到远程仓库，使用命令：git push origin --tags

对于已经提交到远程仓库的tag怎么删除

先删除本地仓库tag

```
git tag -d v0.9
```

再删除远程仓库的tag

```
git push origin :refs/tags/v0.9
```



## GitHub的使用

### 1、常用命令/工具

1）、Fork，将github上开源的仓库Fork到自己的仓库，自己拥有Fork后的仓库的读写权限；

2）、pull request，如果你发现自己fork过来的仓库存在一个bug，并且已经修好，那么可以给原仓库所有者发送一个pull request请求；可以推送pull request给官方仓库来贡献代码。

