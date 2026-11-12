# Print-Camera Resistant Watermarking GitHub 更新说明

本项目的本地目录为 `C:\sys_github\Print-Camera-Resistant-Watermarking`，已关联 [实验室 GitHub 仓库](https://github.com/usst-micslab/Print-Camera-Resistant-Watermarking)。首次上传的提交是 `c38748b`，现有分支是 `main`。本次更新补充了作者仓库对照、数据集入口、辅助模块来源和验证范围。

## 1. 查看并暂存本次更新

在 Windows 的 **CMD 或 Anaconda Prompt** 中执行以下命令：

```bat
cd /d "C:\sys_github\Print-Camera-Resistant-Watermarking"
git status --short --branch
git remote -v
git add README.md GITHUB_UPLOAD_GUIDE_zh.md docs/DATA_AND_PATHS.md docs/DEPENDENCIES.md docs/THIRD_PARTY.md docs/VALIDATION.md
git --no-pager diff --cached --stat
git --no-pager diff --cached --name-only
```

核对远端指向 `usst-micslab/Print-Camera-Resistant-Watermarking`。本次暂存清单应只有上述六份 Markdown 文件。原始论文、数据集、权重、环境和参考代码下载目录位于 Git 提交范围之外。

## 2. 提交并推送

```bat
git commit -m "Document upstream sources and dataset"
git push origin main
```

如果直连 GitHub 失败且本机的 HTTP 代理正监听 `7897`，可用下面这条命令仅为这次推送设置代理：

```bat
git -c http.proxy=http://127.0.0.1:7897 push origin main
```

浏览器出现 GitHub 授权时，用对实验室仓库有写权限的账号登录。如果终端显示 `Repository not found`，先确认该账号能打开实验室仓库。

## 3. 核对更新

在 GitHub 刷新仓库页面，确认 README 顶部显示论文、上游代码和实验数据集三个链接。也可以对照本地与远端 `main` 的提交号：

```bat
git rev-parse HEAD
git ls-remote --heads origin main
```
