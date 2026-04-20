# 维护者备忘

> 这份文件给 ClassWeave 组织维护者看，**不会**被 GitHub 自动渲染到组织主页。

## 推送到 GitHub 的注意事项

本地这个目录叫 `classweave-.github/` 只是为了和兄弟项目并列在 `opensource/`
下方便管理。**真正推送到 GitHub 时，远端仓库名必须严格叫 `.github`**
（前面带点、不带任何前缀），否则 GitHub 不会识别为组织 Profile 仓库：

```bash
cd opensource/classweave-.github
git init
git add .
git commit -m "chore: initial org profile"

# 注意远端仓库名是 .github，不是 classweave-.github
git remote add origin git@github.com:ClassWeave/.github.git
git branch -M main
git push -u origin main
```

推送后，`profile/README.md` 会在几秒内出现在
<https://github.com/ClassWeave> 顶部。

## 目录结构

```
classweave-.github/
├── profile/
│   └── README.md   ← 渲染在 https://github.com/ClassWeave 上
├── LICENSE         ← Apache 2.0
├── README.md       ← 仓库对外说明（点进 .github 仓库会看到）
└── MAINTAINERS.md  ← 你正在看的这份维护者备忘
```

## 想加点什么

GitHub `.github` 仓库还可以承载一些**组织级**的默认配置，例如：

- `CODE_OF_CONDUCT.md` — 组织级行为守则
- `SECURITY.md` — 组织级安全披露政策（覆盖未单独提供该文件的仓库）
- `CONTRIBUTING.md` — 组织级贡献指南
- `ISSUE_TEMPLATE/` 与 `PULL_REQUEST_TEMPLATE.md` — 组织级默认模板
- `FUNDING.yml` — 赞助配置（会出现在所有仓库的 "Sponsor" 按钮里）
- `workflows/` — 组织级可复用 GitHub Actions

目前 ClassWeave 只放了 profile，其余按需添加即可。

## 修改 profile 后的预览

GitHub 不提供 profile 的本地预览端点，但 `profile/README.md` 的语法与
普通仓库 README 完全一致。建议在改完之后：

1. 用 VSCode / Cursor 的 Markdown 预览先肉眼看一遍；
2. push 到 `main`；
3. 打开 <https://github.com/ClassWeave>，刷新两次（GitHub 偶尔要等 30 秒
   左右才会刷新缓存）。
