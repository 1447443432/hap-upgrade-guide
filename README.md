# HAP 升级指南 (HAP Upgrade Guide)

明道云 HAP 私有部署版本升级专属 Skill，用于 WorkBuddy / OpenClaw 生态。

## 功能说明

本 Skill 自动生成 HAP（明道云）私有部署版本的升级文档，支持：

- **升级咨询**：回答版本兼容性、升级路径、附加操作等咨询问题
- **文档生成**：自动生成完整的 Markdown + HTML 升级指南，包含可执行步骤
- **单机/集群双模式**：支持 Docker Compose 单机模式和 Kubernetes 集群模式
- **离线/在线双场景**：根据网络环境生成对应的资源准备步骤
- **AMD64 / ARM64 双架构**：自动适配不同 CPU 架构

## 安装方式

### 方式一：ClawHub 一键安装（推荐）

访问 [ClawHub](https://clawhub.ai/) 搜索 `hap-upgrade` 或直接安装：

```bash
clawhub install hap-upgrade
```

### 方式二：WorkBuddy 内安装

在 WorkBuddy 对话中直接说：
```
帮我安装 HAP升级指南 技能
```

### 方式三：手动导入

1. 下载本仓库全部文件
2. 将 `HAP升级指南` 文件夹放入 `~/.workbuddy/skills/` 目录
3. 重启 WorkBuddy 即可生效

## 使用方法

安装后，在 WorkBuddy 对话中描述你的升级需求即可，例如：

```
帮我生成 HAP 从 v5.6.0 升级到 v7.3.2 的升级文档，
单机模式，AMD64，离线环境
```

Skill 会自动：
1. 抓取官方实时文档（版本发布历史、升级步骤等）
2. 合并跨越路径中的所有附加操作
3. 生成完整 Markdown 文档
4. 自动转换为带侧边目录的 HTML 文档

## 生成的文档包含

- 版本信息总览
- 提前准备（镜像/离线包下载链接）
- 升级前准备（备份、版本确认、前端二开注意事项）
- 升级步骤（分前/中/后三阶段）
- 升级后验证
- 参考文档链接

## 目录结构

```
HAP升级指南/
├── SKILL.md                            # Skill 主文件（核心逻辑）
├── references/
│   ├── command-library.md              # 升级命令库
│   ├── merge-rules.md                  # 跨版本合并规则
│   └── site-structure.md              # 官方文档网站结构
└── assets/
    ├── upgrade-guide-template-standalone.md  # 单机模式模板
    └── upgrade-guide-template-cluster.md     # 集群模式模板
```

## 技术要点

- 严格遵循官方文档，不凭记忆补全版本细节
- 跨版本升级时自动合并路径中所有附加操作
- 文档预览服务使用实际镜像名称（`mingdaoyun-doc`，非官网显示的 `mingdaoyun-doc-preview`）
- 离线包直接给出实际下载链接，不写"请前往官网下载"等模糊说明
- 前端二开注意事项强制包含在升级前准备中

## 要求环境

- WorkBuddy 客户端版本 ≥ v2.3.0（支持 OpenClaw 生态 Skill）
- 或任何兼容 OpenClaw S1 标准的 AI Agent 环境

## 版本历史

| 版本 | 日期 | 说明 |
|------|------|------|
| v1.0.0 | 2026-03 | 初始版本，支持单机和集群模式升级文档生成 |
| v1.0.1 | 2026-03 | 修复 HTML 生成方式，MD 为唯一事实来源 |
| v1.0.2 | 2026-05 | 修正文档预览服务镜像名称规范 |
| v1.0.3 | 2026-05 | 补充 ENV_APP_VERSION 环境变量规范 |
| v1.0.4 | 2026-05 | 新增前端二开注意事项 + 离线包实际下载链接 |

## 许可证

MIT License

## 相关链接

- ClawHub：https://clawhub.ai/
- 明道云私有部署文档：https://docs-pd.mingdao.com/
- WorkBuddy 官网：https://www.codebuddy.cn/

## 问题反馈

如有问题或建议，欢迎提交 Issue 或 Pull Request。
