# 快速开始指南 | Getting Started Guide

欢迎使用 MIGOE 框架！本指南将帮助您快速了解如何使用和贡献本项目。

## 面向不同用户 | For Different Users

### 🔬 研究者：使用 MIGOE 评估您的模型

1. **了解框架**
   - 阅读 [README.md](README.md) 了解 MIGOE 的核心价值和六个核心原则

2. **评估您的研究**
   - 逐一检查六个核心原则
   - 使用每个原则下的 Implementation Checklist

3. **应用框架**
   - **Principle 1**: 准备 Generation Card，记录所有生成过程
   - **Principle 2**: 审计数据分区，确保无泄漏
   - **Principle 3**: 实现基线方法进行对比
   - **Principle 4**: 量化并报告不确定性
   - **Principle 5**: 评估下游生物学任务
   - **Principle 6**: 准备代码、环境和可复现示例

4. **完善文档**
   - 按照框架要求撰写方法和结果部分
   - 确保所有清单项都已完成

### 📚 贡献者：参与框架完善

1. **阅读贡献指南**
   - 仔细阅读 [CONTRIBUTING.md](CONTRIBUTING.md)
   - 了解贡献流程和标准

2. **选择贡献方式**
   - **补充文献**: 使用 [Literature Addition](../../issues/new?template=literature-addition.md) 模板
   - **修订内容**: 使用 [Content Update](../../issues/new?template=content-update.md) 模板
   - **分享案例**: 使用 [Case Study](../../issues/new?template=case-study.md) 模板

3. **提交贡献**
   ```bash
   # Fork 仓库
   # 克隆到本地
   git clone https://github.com/your-username/MIGOE.git
   
   # 创建分支
   git checkout -b feature/your-contribution
   
   # 进行修改
   # ...
   
   # 提交更改
   git add .
   git commit -m "描述您的修改"
   git push origin feature/your-contribution
   
   # 在 GitHub 上创建 Pull Request
   ```

### 👥 审稿人：审查社区贡献

1. **了解审查标准**
   - 学术严谨性
   - 文献支持充分性
   - 内容相关性
   - 格式规范性

2. **参与 PR 审查**
   - 查看 [Open Pull Requests](../../pulls)
   - 提供建设性反馈
   - 帮助改进内容质量

## 常见使用场景 | Common Use Cases

### 场景 1: 发表生成式组学研究论文

**目标**: 确保论文符合领域标准

**步骤**:
1. 使用 README.md 中六个原则的清单检查论文内容
2. 确保每个原则的要求都已满足
3. 在方法部分引用 MIGOE 框架
4. 在补充材料中提供 Generation Card 和完整的实施清单

### 场景 2: 开发临床 AI 系统

**目标**: 建立可信的评估流程

**步骤**:
1. **Principle 1**: 定义系统的成熟度层级，准备透明的生成记录
2. **Principle 2**: 严格审计数据来源，防止训练-测试泄漏
3. **Principle 3**: 与简单基线对比，证明复杂性的必要性
4. **Principle 4**: 实现不确定性量化，标识低置信度区域
5. **Principle 5**: 在临床相关任务上验证生物学有效性
6. **Principle 6**: 准备完整的可复现包，便于监管审查

### 场景 3: 审查他人的生成式组学研究

**目标**: 系统化评估研究质量

**步骤**:
1. 使用 MIGOE 六个原则作为审查清单
2. 检查是否提供了 Generation Card（Principle 1）
3. 验证数据分区的合理性（Principle 2）
4. 评估基线对比的充分性（Principle 3）
5. 检查不确定性量化（Principle 4）
6. 审查下游生物学验证（Principle 5）
7. 确认代码和数据的可获得性（Principle 6）

## 推荐阅读路径 | Recommended Reading Paths

### 路径 1: 快速概览（20分钟）
1. README.md - 浏览概述和六个核心原则标题
2. 查看汇总表格（Summary Table）快速了解要求

### 路径 2: 深度学习（1-2小时）
1. 完整阅读 README.md 中的六个核心原则
2. 重点关注与您研究相关的原则
3. 查看每个原则的 Implementation Checklist

### 路径 3: 实践应用（持续）
1. 根据研究进展使用相应的清单
2. 定期回顾框架要求
3. 在实践中不断完善合规性

## 获取帮助 | Getting Help

### 遇到问题？

- **技术问题**: 创建 [Issue](../../issues/new)
- **使用疑问**: 参与 [Discussions](../../discussions)
- **私密咨询**: 发送邮件至 [project-email@example.com]

### 保持更新

- ⭐ Star 本仓库以关注更新
- 👀 Watch 仓库以接收通知
- 📢 关注项目公告

## 社区资源 | Community Resources

- **文档**: 本仓库的所有 Markdown 文件
- **讨论区**: [GitHub Discussions](../../discussions)
- **问题追踪**: [GitHub Issues](../../issues)
- **贡献者**: [CONTRIBUTORS.md](CONTRIBUTORS.md)

## 引用 MIGOE | Citing MIGOE

如果 MIGOE 对您的研究有帮助，请引用：

```bibtex
@misc{migoe2026,
  title={MIGOE: Minimum Information for Generative Omics Evaluation},
  author={[Author Team]},
  year={2026},
  howpublished={\url{https://github.com/[username]/MIGOE}},
  note={A community-driven framework for establishing trust boundaries in generative omics}
}
```

## 下一步 | Next Steps

- [ ] 阅读 [README.md](README.md) 掌握框架完整内容和六个核心原则
- [ ] 使用 Implementation Checklists 评估您的研究
- [ ] 查看 [CONTRIBUTING.md](CONTRIBUTING.md) 了解如何贡献
- [ ] 加入 [Discussions](../../discussions) 与社区交流

---

**欢迎来到 MIGOE 社区！** 让我们共同推动生成式组学的可信发展。
