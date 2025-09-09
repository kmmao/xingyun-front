# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是星云 ERP 前端项目，基于 Vue 3 + Ant Design Vue 4 + vxe-table 构建的企业资源管理系统。

## 开发环境要求

- Node.js v20.17.0+
- pnpm 9.7.1+ (必须使用 pnpm，不支持 npm/yarn)
- 后端服务默认运行在 http://localhost:8080

## 常用开发命令

```bash
# 安装依赖
pnpm bootstrap

# 启动开发服务器
pnpm dev

# 构建项目
pnpm build

# 类型检查
pnpm type:check

# 代码检查和修复
pnpm lint
pnpm lint:eslint
pnpm lint:prettier
pnpm lint:stylelint

# 预览构建结果
pnpm preview
```

## 项目架构

### 技术栈
- **Vue 3.3.4** - 渐进式 JavaScript 框架
- **TypeScript** - 类型安全
- **Vite 4** - 构建工具
- **vue-vben-admin** - 基础框架
- **Ant Design Vue 4.0.7** - UI 组件库
- **vxe-table 4.7.30** - 表格组件
- **Pinia 2.1.4** - 状态管理
- **Vue Router 4** - 路由管理
- **axios** - HTTP 客户端
- **echarts** - 图表库

### 核心目录结构
```
src/
├── api/                 # API 接口定义，按业务模块组织
├── components/          # 公共组件库
├── views/              # 页面组件，按业务模块组织
├── router/             # 路由配置
├── store/              # Pinia 状态管理
├── locales/           # 国际化文件
├── utils/             # 工具函数
└── main.ts            # 应用入口

packages/               # 内部工具包
├── hooks/             # Vue Composition API hooks
└── types/             # TypeScript 类型定义
```

### 业务模块架构
项目采用模块化架构，主要业务模块包括：
- `base-data/` - 基础数据管理（客户、供应商、商品等）
- `sc-stock/` - 库存管理
- `settle/` - 结算管理
- `retail/` - 零售管理
- `development/` - 开发工具
- `system/` - 系统管理

### API 层组织
API 接口按业务模块组织，每个模块包含：
- `index.ts` - API 方法定义
- `model/` - TypeScript 类型定义 (VO/BO/DTO)

### 组件开发规范
- 使用 Vue 3 Composition API
- 组件采用 `<script setup>` 语法
- 严格的 TypeScript 类型定义
- 统一的命名规范：PascalCase for components

### 构建和部署
- 使用 Turbo 进行 Monorepo 管理
- 支持多环境构建：development/test/production/demo/docker
- 代理配置：开发环境 API 请求代理到 http://localhost:8080
- 使用 Hash 路由模式

### 代码质量
- ESLint + Prettier + Stylelint 三重代码检查
- Husky + lint-staged 提交前检查
- TypeScript 严格模式
- Commitizen 规范提交信息

## 开发注意事项

1. **包管理器**：必须使用 pnpm，项目已配置 `preinstall` 检查
2. **类型检查**：开发时运行 `pnpm type:check` 确保类型正确
3. **代码风格**：遵循项目 ESLint/Prettier 配置
4. **组件复用**：优先使用 `src/components/` 中的公共组件
5. **API 调用**：使用 `src/api/` 中定义的接口方法
6. **路由守卫**：已配置路由守卫，注意权限控制