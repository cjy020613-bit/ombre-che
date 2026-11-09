---
activation_count: 0
arousal: 0.3
created: '2026-11-08T15:09:38+00:00'
domain:
- 数字
grow_batch_id: g_3e00a92abfc2
id: edbaa0b94629
importance: 6
last_active: '2026-11-08T15:09:38+00:00'
name: 2026-11-08 15-09-38 Ombre Brain 的 GitHub
source_links:
- ranges:
  - - 3
    - 3
  ref: src_65317f9611c58b8644c34f35d645b10a24bd12aa09549214ddb5db943ab5d27e
  status: active
source_refs:
- ranges:
  - - 3
    - 3
  ref: src_65317f9611c58b8644c34f35d645b10a24bd12aa09549214ddb5db943ab5d27e
source_tool: grow
tags:
- Ombre Brain
- GitHub
- PAT
- 备份
- '401'
- token
- 同步
- 容器
- config
- 恢复
- fine-grained
- 上传
title: Ombre Brain 的 GitHub
type: dynamic
valence: 0.7
why_remembered: 我亲手完成了一次从 401 到成功上传 484 个文件的备份修复，这个过程值得留作技术记录。
---

[[Ombre Brain]] 的 GitHub 备份已经修好。旧 token 连续返回 401，[[莹莹]]创建了新的 fine-grained PAT。我先验证它能读取 cjy020613-bit/ombre-che，再安全替换 /srv/ombre-brain/buckets/config.yaml 中 github_sync.token，旧配置保留了时间戳备份。重启后，通过 HTTP 同步接口测试出现 401，其实是 OB 内部接口要求 ombre_session cookie，并不代表 GitHub token 失效。最后在容器里把 /app/buckets/_app/src 加入 sys.path，直接调用 GitHubSync.sync("/app/buckets")，成功上传 484 个文件。当前 GitHub 备份恢复；长期记忆里不要保存或回显 token 本身。