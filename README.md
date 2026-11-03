# MultiModal Research Daily · 多模态前沿科研日报

公开中文多模态研究站：每天最多精选 5 篇经过核查的真实论文，关注模型架构、特征表示、跨模态融合、数据集及其对舰船识别的迁移启发。

## 🌐 公共网站

网站预期地址： https://wangjingxing0320.github.io/Day-puts/

首次部署前，需在仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。随后打开 **Actions → Publish MultiModal Research Daily** 查看执行状态。GitHub Pages 可能需要数分钟完成发布。

## 已上线的界面功能

- 手机、平板、桌面自适应布局及深浅色切换。
- 多模态论文首页、按研究模块筛选、搜索、归档。
- 论文详情：研究问题、核心方法与数据流、技术改进、实验依据、局限和舰船识别研究启发。
- 原始论文、开源代码和数据集链接（仅在数据实际提供时展示）。
- 响应式分享链接及永久入口。
- 网站不伪造论文：初始 `data/content.json` 为空，未接入真实科研数据前明确显示空状态。

## 数据格式

网站读取仓库根目录的 `data/content.json`：

```json
{
  "schema_version": "1.0.0",
  "updated_at": null,
  "papers": [],
  "issues": []
}
```

每条论文需要 `paper_id`、`metadata`、`classification`、`analysis`、`evidence`、`review` 和 `display` 字段。只有 `review.review_status === "approved"` 的论文才会展示；日报需要 `paper_ids` 关联论文。

## 后续真实论文更新

当前仓库**已配置网站自动发布，不代表已经配置自动论文采集和审核**。

真实更新下一阶段需要：
1. 采集 arXiv 等可信来源并获取可解析论文全文。
2. 使用安全保存在 GitHub Actions Secrets 中的 AI API 密钥进行分析与独立审核。
3. 通过永久 ID 去重、源证据检查、正式发表状态检查。
4. 更新 `data/content.json` 并自动触发 Pages 发布。

不允许在仓库中写入 API 密钥。任何科研结论请以论文原文为准。

## 本地预览

直接运行 `python -m http.server 8000`，浏览器打开 http://localhost:8000。

## 维护和分享

GitHub 源码：https://github.com/wangjingxing0320/Day-puts
