# Print-Camera Resistant Watermarking：首次上传 GitHub

本项目目录：`C:\sys_github\Print-Camera-Resistant-Watermarking`。`C:\sys_github` 是多个项目的上级目录，**不要在上级目录初始化 Git 或把多个项目一起上传**。

当前只整理了现有源码和说明，没有安装依赖、修复缺失模块、创建远端或上传。README 已标明这不是可直接运行的完整版本。上传源码不代表论文复现成功；若要公开，先确认实验室及第三方代码的发布权限。

## 1. 建立本项目的空仓库

在 GitHub 新建空仓库，仓库名可用 `Print-Camera-Resistant-Watermarking`，按需选择公开或私有。不要自动添加 README、License 或 `.gitignore`。新建后复制它的 HTTPS 地址；不要复用 PCMark-NAS 或其他论文的仓库地址。

如果要助手继续上传，只需把新仓库地址发回，不必先执行下面的命令。

## 2. 使用 CMD 检查待上传文件

如果选择自己手动上传，在 **CMD（命令提示符）** 执行：

```bat
cd /d "C:\sys_github\Print-Camera-Resistant-Watermarking"
git init -b main
git add .
git --no-pager diff --cached --stat
git --no-pager diff --cached --name-only
```

不要复制终端提示符。仅在首次初始化时执行 `git init`。暂存清单应只包含两份源码、文档、论文标题图、校验值和 `.gitignore`。不得出现完整 PDF、原始压缩包、`dataset/`、两组配对图像、TensorFlow checkpoint/SavedModel、环境或日志。`.gitignore` 不会移除已经被 Git 跟踪的文件；发现异常先停下核对，不要删原件或强制推送。

## 3. 提交并绑定新仓库

若 Git 提示提交身份缺失，先配置本仓库的姓名和邮箱。例如沿用此前提供的提交身份时：

```bat
git config --local user.name "usst-micslab"
git config --local user.email "usst-micslab@163.com"
```

这只影响当前仓库。确认暂存文件无误后提交：

```bat
git commit -m "Archive supplied print-camera watermarking source"
```

把以下 `https://github.com/OWNER/REPOSITORY.git` **整条替换**成刚创建的真实地址：

```bat
git remote add origin https://github.com/OWNER/REPOSITORY.git
git remote -v
git push -u origin main
```

如果远端已绑定，就先核对地址，不重复添加。需要浏览器授权时按提示完成，不把 token 写进聊天、README 或 URL。若当前确实开启了端口为 7897 的本地代理，可仅为这次推送使用：

```bat
git -c http.proxy=http://127.0.0.1:7897 push -u origin main
```

当前电脑未开代理或端口不同，不要照抄该代理命令。不要修改全局 Git 设置来处理单个项目。

## 4. 核实上传与后续更新

刷新新仓库，应看到英文 README、标题图、两份 Python 文件和缺失依赖说明。可在 CMD 对照本地与远端提交：

```bat
git rev-parse HEAD
git ls-remote origin refs/heads/main
git status -sb
```

提交号一致且没有待提交改动，说明当前版本同步。以后有修改时，在同一个项目目录中按“暂存 → 检查清单 → 提交 → 推送”操作，不重复初始化或添加 origin。`nothing to commit, working tree clean` 在没有新改动时不是错误；若远端已有不同历史或推送被拒，先查明原因，不使用 `--force`。

本项目尚未运行验证，具体边界见 [验证记录](docs/VALIDATION.md) 和 [已知问题](docs/KNOWN_ISSUES.md)。
