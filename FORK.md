# FORK.md — 本仓库与上游的关系

| 项 | 值 |
|---|---|
| 上游项目 | [YuJunZhiXue/dsh-purge](https://github.com/YuJunZhiXue/dsh-purge) |
| 原作者 | YuJunZhiXue（Copyright 2026，见 [NOTICE](./NOTICE)） |
| 上游版本基线 | 1.1.85（本 fork 的 `package.json` 版本号与上游一致，未改） |
| 本 fork | [Sealkeeper/dsh-purge](https://github.com/Sealkeeper/dsh-purge) |
| 许可证 | Apache-2.0（[LICENSE](./LICENSE)），[NOTICE](./NOTICE) 原样保留，未做任何删改 |

## 这个 fork 改了什么

只改“指向哪里”，不改插件行为：

1. `package.json` —— `repository` / `homepage` / `bugs` 与 `dsh.install.{tarball,zip,git}` 指向本 fork。
2. `README.md` / `README.zh-CN.md` —— 安装、克隆、Releases 相关 URL 指向本 fork；顶部加了一段 fork 声明；作者署名段、署名要求段、许可证段的上游链接一字未动。
3. `.github/workflows/release.yml` —— 发布 job 的 `github.repository` 守卫改成当前仓库，使 tag/Release 在本 fork 下可跑；产物名、`release-notes.md` 首行校验逻辑未改。

## 这个 fork 没改什么

- `lib/**`、`bin/**`、`client.js`、`presets/**`、`scripts/**`、`cordis.patch.yml`、`docs/**`（见下条）、`release-notes.md`、`LICENSE`、`NOTICE`、`LICENSE-COMMERCIAL.md`、`screenshots.json`：与上游 1.1.85 安装包逐字节一致。
- `docs/notice/`（上游包内的 4 张第三方聊天/直播截图）**未随本 fork 发布**：这些图片未被任何文档引用，且涉及无关个人的私聊与直播画面，不重复分发。功能无影响。
- 新增 `FORK.md`、`.gitattributes`（固定 LF，避免 Windows 下换行改动让 diff 与上游失真）。
- 插件 ID 仍是 `dsh-purge`，命令仍是 `dsh-purge` / `/purge`。与上游版本**不要同时安装**，两者会在 `$DSH_HOME` 下争用同一套 apply/revert 状态。

## 上游对二开的要求（照抄上游 README 的口径）

- 原版不允许倒卖；本 fork 同样不收费、不白标、不挂群出售。
- 二开必须署名，写明来源仓库 `YuJunZhiXue/dsh-purge`，并保留 `NOTICE`。
- 隐瞒来源、改头换面据为己有，上游作者按侵权处理。

## 同步上游

```sh
git remote add upstream https://github.com/YuJunZhiXue/dsh-purge.git
git fetch upstream --tags
git log --oneline HEAD..upstream/master
```

上游新版本发布后，按 `release-notes.md` 的变更重放本文件列出的 3 处 URL/守卫改动即可。
