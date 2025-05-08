## 关于Git用户名

可使用 `git config` 命令更改与 Git 提交关联的名称。 你设置的新名称将在从命令行推送到 GitHub 的任何未来提交中显示。 如果您想要将真实姓名保密，则可以使用任意文本作为您的 Git 用户名。

使用 `git config` 更改与 Git 提交关联的名称仅影响未来的提交，而不会更改用于过去提交的名称。

## 为计算机上的所有仓库设置Git用户名

1. 打开Git Bash。
2. 设置Git用户名：
```shell
git config --global user.name "xyz-liu15"
```
3. 确认你正确设置了Git用户名：
```shell
git config --global user.name
> xyz-liu15
```

## 为一个仓库设置Git用户名

1. 打开Git Bash。
2. 将当前工作目录更改为你想要在其中配置与Git提交关联的名称的本地仓库。
3. 设置Git用户名：
```shell
git config user.name "xyz-liu15"
```
4. 确认你正确设置了Git用户名：
```shell
git config user.name
> xyz-liu15
```

