# DeGate Docs — 写作与协作规则

本仓库通过 GitBook Git Sync 驱动 docs.degate.com。`multichain-platform` 分支 = 线上；`v2-rewrite` 分支 = 重写稿。

## Git 流程

- 仓库历史很大，克隆必须用：`git clone --depth 1 --single-branch --branch <branch>`。
- **每次编辑前先 `git pull`**：团队成员可能在 GitBook UI 里编辑，会以 `GITBOOK-N` 提交回写到分支。
- 推送到同步分支 = 直接改线上，改动要小步快推。

## GitBook 约定

- `SUMMARY.md` 是唯一目录，新页面必须登记，否则不显示；首页 = `README.md`。
- 文件路径 = URL slug。**改名或移动文件 = 换 URL**，必须同时在 `.gitbook.yaml` 的 `redirects:` 加一条旧路径映射。
- GitBook 专有语法：`{% hint style="info" %}...{% endhint %}`、`{% file src="..." %}`、`{% embed url="..." %}`。图片放 `.gitbook/assets/`。

## 内容纪律

- **"broker" 及变体（brokerage 等）绝不出现在任何对外文本**（监管红线）。实体类别统一为 self-custody multichain crypto wallet。
- **只写已上线的功能**。未上线功能不进文档；roadmap 内容一律不写。
- 未经第一手验证的事实用 `> ⚠️ [NEEDS VERIFICATION: ...]` 占位，发布（merge 到 multichain-platform）前必须全部清零：`grep -rn "NEEDS VERIFICATION" .`
- 费率、数字带 "as of [月份 年份]" 限定；不使用绝对化措辞（every/always/only/never），除非事实必然。
- 不写与竞品的比较性 claim；不写风控/安全方面尚未实现的承诺。
- 语言基准：以一线钱包/工具类产品文档为范例，直接、面向读者（"you"）、每页开头一段可独立摘取的定义（GEO 需要），其后正常人类行文。避免营销腔和破折号（em dash）。
- 每次结构性改动后做一致性扫描：绝对化措辞、数字精度、范畴边界。

## 发布检查清单（merge 前）

1. `grep -rn "NEEDS VERIFICATION" .` 结果为空
2. `grep -rni "broker" .` 结果为空（本文件除外）
3. 新增/改名页面已登记 SUMMARY.md，旧 URL 已加 redirects
4. 产品声明经 Eva 审核（费率、支持链、功能状态）
