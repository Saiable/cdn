# cdn
cdn for web



[learning-station/git基础及协同开发.md at tools · Saiable/learning-station (github.com)](https://github.com/Saiable/learning-station/blob/tools/git/git基础及协同开发.md)



# git tag

[(18条消息) GIT TAG的使用_OceanSky6的博客-CSDN博客_git tag 用法](https://blog.csdn.net/yaomingyang/article/details/78839295)

## 一、tag

tag用于在开发阶段创建标签，某个阶段完成了创建一个版本，在开发中可以使用tag来指定软件的一个重要时期，比如版本号更新的时候可以创建一个version1.0，这样回顾的时候比较简单；

基本操作有查看tag、创建tag、验证tag、共享tag

## 二、查看tag

列出所有的tag:

```bash
git tag
```


这样列出的tag是按照字母排序的，和创建时间没有关系，如果只是想查看某些tag的话可以加一些限定：

```bash
git tag -l version1.*
```

这样只会列出1.几的版本

## 三、创建tag

创建轻量级tag:

```bash
git tag version 1.0  也可以 git tag 1.0
```

带有信息的tag:

```bash
git tag -a version1.0 -m 'first version'
```

用 -a （译注：取 annotated 的首字母）指定标签名字即可,而 -m 选项则指定了对应的标签说明，Git 会将此说明一同保存在标签对象中。如果没有给出该选项，Git 会启动文本编辑软件供你输入标签说明；

可以使用 git show 命令查看相应标签的版本信息，并连同显示打标签时的提交对象。

查看以前的commit命令：

```bash
git log --oneline
```

## 四、删除tag

很简单，知道tag名称：

```bash
git tag -d v1.0
```

## 五、共享tag

我们git push的时候tag是不会提交到服务器的，所以我们需要这样做：

```bash
git push origin --tags
```

## 六、查看tag信息

查看本地的tag和分支信息：

```bash
 git show-ref
 57cd76537dcc6bf746ff53a9043c9fb7e4a899e refs/heads/dev
b846e1798451b1e32c36fdbd18496a914d8747c1 refs/heads/devyao
8031934f0ec7a7cb1b6a3abac5826486ae252a6b refs/heads/imag
964451db22ad74ebad1c212086576a612b844141 refs/heads/liv
21a6aefd948f9f5fdf857a07d05c20ac718ca3d2 refs/heads/master
7ce1f9941f5b822ff3e158a32b0ed3d37c9ee1fe refs/heads/pr
a457efac207a921d928676c2e1de6675809d157e refs/heads/wl
a07cc0dc27266a02f83d219fb874ad5af4d581c1 refs/heads/yut
d9beb683718b0dea0e0020fe58f0426eb3e4a64c refs/remotes/origin/20
21a6aefd948f9f5fdf857a07d05c20ac718ca3d2 refs/remotes/origin/HE
c2a252b4d72314a7b355f36cad9156728c43ffb2 refs/remotes/origin/de
d34203673008a2ae4215ab044ec8d750b2c527ad refs/remotes/origin/de
b846e1798451b1e32c36fdbd18496a914d8747c1 refs/remotes/origin/de
1e379a53efcf7eaebe1d1ca7ab882565d20b03db refs/remotes/origin/gg
463bdba451f7e6eaa761e3c8d7b14516d2547eee refs/remotes/origin/gg
0a8a158425a55efc431b5b91020e2079ab8e9404 refs/remotes/origin/gg
1ac4e159bf1a5d56401868c8d50abb81542919d6 refs/remotes/origin/gr
67bb6ef3e104ae7343e3e7a08f7def7ed4f2ea2c refs/remotes/origin/gw
aed583590988c8856bce285db380ad537ef8774c refs/remotes/origin/im
e2630203ee3b84da18565cda1cb01186288b7c2a refs/remotes/origin/li
e19106372ab0ed33b8ab93f53847865d00b6d114 refs/remotes/origin/li
00eb3b8908b72ef12183ff22e44559d4f1ef64b8 refs/remotes/origin/lv
21a6aefd948f9f5fdf857a07d05c20ac718ca3d2 refs/remotes/origin/ma
d6080b0cbfc971ed1e09334dcb431f2c8065bc0b refs/remotes/origin/mj
7ce1f9941f5b822ff3e158a32b0ed3d37c9ee1fe refs/remotes/origin/pr
abf400db76b3c13048c5dc771b6e4d6291098db6 refs/remotes/origin/to
252aa50232732989fdf8b038b104d4cb0d81d0ce refs/remotes/origin/ts
bb1302598207be8bb9deb7ea1d7a45262706b057 refs/remotes/origin/wj
a457efac207a921d928676c2e1de6675809d157e refs/remotes/origin/wl
55f9853aa803596312063b84d2dc6d0ad8e54638 refs/remotes/origin/wu
47b4d4ac6df056fc3ba2e4377061b641eee33e4b refs/remotes/origin/xi
170a94666914634080d57eee207312bb103e48ea refs/remotes/origin/yp
e5a5bfcb5b7332dd0a2fd79408f8650c1084d417 refs/remotes/origin/yu
a0523b3ac3bdd87eb7e45498af66fac304fa34bc refs/remotes/origin/zh
022a9c32610e25d6eda197a7d86b25ce9ba518a7 refs/remotes/origin/zh
c72c458d62b293aaba12964b52dd540e22089644 refs/remotes/origin/zx
78d8e17322feeafd836dd2921582f802e6cc313d refs/tags/v1.0

```

删除远程服务器端的tag:

```bash
git push origin --delete tag <tagname>
```



```bash
 git push origin --delete tag v1.0
 o git@gitlab.gofund.cn:terminal_new/gogoalback.git
 - [deleted]         v1.0
```

也可以推送一个空的tag:

删除本地tag，然后推送一个空的tag到远程服务器：

```bash
git tag -d <tagname>
git push origin :refs/tags/<tagname>
```

查看远程分支及tag:

```bash
  git ls-remote origin
 46cec519b47977c519f939c5ed0a23c1dbddee0        HEAD
d9beb683718b0dea0e0020fe58f0426eb3e4a64c        refs/heads/2017
1764939fc2edcaffbb70b4abe428a40b6c9ec733        refs/heads/dev
d34203673008a2ae4215ab044ec8d750b2c527ad        refs/heads/dev_c
b846e1798451b1e32c36fdbd18496a914d8747c1        refs/heads/de
1e379a53efcf7eaebe1d1ca7ab882565d20b03db        refs/heads/gg
463bdba451f7e6eaa761e3c8d7b14516d2547eee        refs/heads/ggm
0a8a158425a55efc431b5b91020e2079ab8e9404        refs/heads/ggp
1ac4e159bf1a5d56401868c8d50abb81542919d6        refs/heads/gra
67bb6ef3e104ae7343e3e7a08f7def7ed4f2ea2c        refs/heads/gw
aed583590988c8856bce285db380ad537ef8774c        refs/heads/image
e2630203ee3b84da18565cda1cb01186288b7c2a        refs/heads/liv
00eb3b8908b72ef12183ff22e44559d4f1ef64b8        refs/heads/lv
346cec519b47977c519f939c5ed0a23c1dbddee0        refs/heads/master
d6080b0cbfc971ed1e09334dcb431f2c8065bc0b        refs/heads/mj
7ce1f9941f5b822ff3e158a32b0ed3d37c9ee1fe        refs/heads/pro
abf400db76b3c13048c5dc771b6e4d6291098db6        refs/heads/top1
252aa50232732989fdf8b038b104d4cb0d81d0ce        refs/heads/tsd
bb1302598207be8bb9deb7ea1d7a45262706b057        refs/heads/ws
a457efac207a921d928676c2e1de6675809d157e        refs/heads/wl
55f9853aa803596312063b84d2dc6d0ad8e54638        refs/heads/wuz
47b4d4ac6df056fc3ba2e4377061b641eee33e4b        refs/heads/xiong
e5a5bfcb5b7332dd0a2fd79408f8650c1084d417        refs/heads/yut
346cec519b47977c519f939c5ed0a23c1dbddee0        refs/heads/zhoug
022a9c32610e25d6eda197a7d86b25ce9ba518a7        refs/heads/zhou
c72c458d62b293aaba12964b52dd540e22089644        refs/heads/zxd
d5aa05b4f45ef702bfa97a0982cc8c2c94ce6994        refs/remotes/origin/yut
78d8e17322feeafd836dd2921582f802e6cc313d        refs/tags/v1.0
85ea322c02b5ff1ffe15b693fc1a79d03fc328a8        refs/tags/v1.0^{}
```







# 流程

1.本地文件更新

2.commit之后

3.`git log`获取commit的id

4.git tag

