# 贡献指南 | Contributing Guidelines

感谢您对 MIGOE 框架的关注！我们欢迎来自学术界和工业界的贡献，共同完善生成式组学的评估标准。

## 贡献原则 | Contribution Principles

### 学术严谨性
- 所有贡献必须基于已发表的同行评审文献或经过充分验证的实践经验
- 引用文献时请使用标准格式（APA、Nature 或领域通用格式）
- 避免未经验证的观点或商业宣传

### 社区协作
- 尊重现有内容的结构和风格
- 重大修改前请先开启 Issue 讨论
- 保持专业、建设性的沟通态度

### 可持续维护
- 提交的内容应具有长期价值，而非针对特定工具的临时性描述
- 优先考虑方法论和原则性指导，而非具体实现细节

## 贡献方式 | How to Contribute

### 1. 报告问题 | Report Issues

如果您发现以下问题，请创建 Issue：
- 内容错误或过时信息
- 文献引用不准确
- 章节逻辑不清晰
- 技术术语使用不当

**Issue 模板**：
```markdown
**问题类型**: [内容错误 / 文献更新 / 结构建议 / 其他]
**涉及章节**: Chapter X - [章节名称]
**问题描述**: 
**建议修改**: 
**参考文献**: (如适用)
```

### 2. 补充文献 | Add References

为章节添加相关文献引用：

1. Fork 本仓库
2. 在相应章节的 `references.md` 文件中添加文献
3. 使用统一格式：
   ```markdown
   - **[作者姓名] et al. (年份)**. 文章标题. *期刊名*, 卷(期), 页码. DOI: [链接]
     - **关键贡献**: 简要说明该文献对本章节的价值
   ```
4. 提交 Pull Request

### 3. 修订章节内容 | Revise Chapter Content

对章节进行实质性修改时，请遵循以下流程：

#### Step 1: 开启讨论
在 [Discussions](../../discussions) 或 Issue 中说明：
- 修改动机（为什么需要这个改动？）
- 修改范围（涉及哪些章节？）
- 预期影响（对框架整体的影响？）

#### Step 2: Fork 与分支
```bash
# Fork 仓库后克隆到本地
git clone https://github.com/Li-OmicsLab-MPU/MIGOE-Checklist.git
cd MIGOE

# 创建特性分支
git checkout -b feature/chapter-X-improvement
```

#### Step 3: 进行修改
- 保持 Markdown 格式一致性
- 每个章节应包含：
  - **背景与动机**
  - **核心概念定义**
  - **评估方法/标准**
  - **实施建议**
  - **参考文献**
- 新增内容必须附带文献支持

#### Step 4: 自我审查清单
- [ ] 内容符合生成式组学的审计标准
- [ ] 所有陈述有文献或实践依据
- [ ] 术语使用准确且一致
- [ ] Markdown 格式正确（无断链、图片可访问）
- [ ] 引用格式统一
- [ ] 无拼写或语法错误

#### Step 5: 提交 Pull Request
```bash
git add .
git commit -m "feat(chapter-X): 简要描述修改内容"
git push origin feature/chapter-X-improvement
```

在 GitHub 上创建 PR，并填写：
- **修改摘要**: 简要说明改动内容
- **变更理由**: 为什么需要这个修改
- **影响范围**: 涉及哪些章节
- **参考文献**: 支持修改的关键文献

### 4. 贡献案例研究 | Contribute Case Studies

我们特别欢迎实际应用案例：

**案例要求**：
- 真实的研究场景（可匿名化）
- 明确的问题定义与解决方案
- 使用 MIGOE 框架的具体方式
- 结果与经验总结

**提交格式**：
在 `chapters/chapter-8-case-studies.md` 中添加：
```markdown
### 案例 X: [案例标题]

**研究背景**: 
**应用场景**: 
**MIGOE 应用**: 
**关键发现**: 
**经验教训**: 
**参考文献**: 
```

## Pull Request 审查流程 | PR Review Process

1. **自动检查**: CI 会验证 Markdown 格式和链接有效性
2. **社区审查**: 维护者和社区成员会审查内容质量
3. **讨论与修订**: 根据反馈进行必要的修改
4. **合并**: 通过审查后，维护者将合并 PR

**审查标准**：
- ✅ 学术严谨性
- ✅ 内容相关性
- ✅ 文献支持充分
- ✅ 格式规范
- ✅ 与现有内容协调

## 行为准则 | Code of Conduct

请阅读我们的 [行为准则](CODE_OF_CONDUCT.md)，确保社区的专业性和包容性。


## 需要帮助？ | Need Help?

- 📖 查看 [README.md](README.md) 了解项目概况
- 💬 在 [Discussions](../../discussions) 提问
- 📧 联系维护者: [kefengl@mpu.edu.mo]

---

**再次感谢您的贡献！** 每一个改进都让 MIGOE 框架更加完善，为生成式组学的可信发展贡献力量。
