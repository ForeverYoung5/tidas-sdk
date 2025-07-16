# TIDAS TypeScript SDK

[English](README.md) | [中文](README-zh.md)

一个用于 ILCD/TIDAS 数据管理的 TypeScript SDK，为生命周期评估（LCA）数据结构提供类型安全的数据操作。

## 🚀 快速开始

### 安装

```bash
npm install @tiangong-lca/tidas-sdk
```

### 基本用法

```typescript
import { createContact, createFlow } from '@tiangong-lca/tidas-sdk/core';
import { Contact, Flow } from '@tiangong-lca/tidas-sdk/types';

// 创建新的联系人
const contact = createContact();
contact.contactDataSet.contactInformation.dataSetInformation['common:name'] = [
  { '@xml:lang': 'zh', '#text': '张博士' }
];

// 验证联系人数据
const validation = contact.validate();
console.log('数据有效:', validation.success);

// 转换为 JSON
const json = contact.toJSONString(2);
```

## 📦 包结构

SDK 为不同的使用场景提供了多个入口点：

```typescript
// 核心功能（推荐）
import { createContact, createFlow } from '@tiangong-lca/tidas-sdk/core';

// 类型定义
import { Contact, Flow } from '@tiangong-lca/tidas-sdk/types';

// 用于验证的 Zod 模式
import { ContactSchema } from '@tiangong-lca/tidas-sdk/schemas';

// 工具函数
import { objectUtils } from '@tiangong-lca/tidas-sdk/utils';

// 全部导入（方便但包体积较大）
import * from '@tiangong-lca/tidas-sdk';
```

## 🏗️ 功能特性

- **类型安全**：基于 ILCD 模式生成的完整 TypeScript 支持
- **运行时验证**：基于 Zod 的验证，支持可配置模式
- **8 种实体类型**：支持所有核心 TIDAS 实体
- **JSON 互操作性**：对象与 JSON 之间的无缝转换
- **批量操作**：高效处理多个实体
- **多语言支持**：内置多语言文本字段支持
- **性能优化**：为性能关键场景提供可配置验证

## 📚 示例

`examples/` 目录包含了全面的使用示例。运行示例：

```bash
cd examples
npm install
npm run run-basic  # 基本实体使用
```

详细信息请参见 [examples/README.md](examples/README.md)。

## 🔧 开发

此仓库包含 SDK 的源代码。示例使用已发布的 npm 包。

### 构建命令

```bash
npm run build          # 编译 TypeScript
npm run dev            # 监视模式
npm run generate-types # 从模式生成类型
npm run test           # 运行测试
npm run lint           # 代码检查
```

## 🤝 贡献

1. Fork 仓库
2. 创建功能分支
3. 进行更改
4. 添加测试和示例
5. 提交 Pull Request

## 📄 许可证

MIT 许可证 - 详情请参见 [LICENSE](LICENSE) 文件。

## 🏷️ 版本

当前版本：0.1.1

## 🔗 链接

- [npm 包](https://www.npmjs.com/package/@tiangong-lca/tidas-sdk)
- [GitHub 仓库](https://github.com/tiangong-lca/tidas-sdk)