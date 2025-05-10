
您可以使用 `git config` 命令来更改与您的 Git 提交相关联的电子邮件地址。您设置的新电子邮件地址将在您从命令行推送任何未来的提交到 GitHub 时可见。在更改提交电子邮件地址之前您所做的任何提交仍然与您之前的电子邮件地址相关联。

## 为您的计算机上的每个存储库设置电子邮件地址

1. 打开Git Bash。
2. 在Git中设置一个邮箱地址。你可以使用任何电子邮件地址。
```shell
git config --global user.email "xyz.liu15@gmail.com"
```
3. 确认你已在Git中正确设置了电子邮件地址：
```shell
git condig --global user.email
> xyz.liu15@gmail.com
```
4. 将邮箱地址添加到你的 GitHub 账户，以便您的提交被归因于你，并在你的贡献图中显示。

## 为单个仓库设置邮箱地址

GitHub 使用您在本地 Git 配置中设置的邮箱地址，将命令行推送的提交与您的 GitHub 账户关联起来。

您可以更改与单个存储库中的提交相关联的电子邮件地址。这将覆盖此存储库中的全局 Git 配置设置，但不会影响任何其他存储库。

1. 打开Git Bash。
2. 将当前工作目录更改为您要配置与 Git 提交相关联的电子邮件地址的本地存储库。
3. 在Git中设置一个邮箱地址。你可以使用任何电子邮件地址。
```shell
git config user.email "xyz.liu15@gmail.com"
```
4. 确认你已在Git中正确设置了电子邮件地址：
```shell
git config user.email
> xyz.liu15@gmail.com
```
5. 将邮箱地址添加到你的 GitHub 账户，以便您的提交被归因于你，并在你的贡献图中显示。
