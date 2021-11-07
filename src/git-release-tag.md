# Gite Release 和tag操作手册



## TAG 使用

https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E6%89%93%E6%A0%87%E7%AD%BE


``` javascript

git tag  //查看当前的tag标签信息

// git tag -a v1.4 -m 'my version 1.4' //发布一个V1.4的tag标签，-m后面是注释

// git tag -a V0.17.0 -m '用于开发使用的文章内容。以后的内容都会在这个不停的重构。重构完毕后发布2.0'

git tag V0.17.0 //快速打标签

git tag -d V0.17.0 ///*删除本地tag*/

git push origin --delete tag 0.1.1 //删除远程服务器上的TAG

git push origin V0.17.0 //推送指定tag到远程
git push origin --tags //推送所有的tag到远程

```

### 轻量级标签
轻量级标签实际上就是一个保存着对应提交对象的校验和信息的文件。要创建这样的标签，一个 -a，-s 或 -m 选项都不用，直接给出标签名字即可：
``` html
$ git tag v1.4-lw
$ git tag
v0.1
v1.3
v1.4
v1.4-lw
v1.5
```

## 个人操作流程

```
git push origin --delete tag V0.17.0

git tag -d V0.17.0 

git tag

git tag V0.17.1

git push origin V0.17.1 




```




