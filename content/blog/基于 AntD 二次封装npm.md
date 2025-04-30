---
title: 基于 Antd 二次开发，打造符合业务场景的 React 组件库
date: 2025-04-29 19:49:58
tags: ["React", "Ant Design", "Component Library", "DXP", "Frontend"]
series: ["前端开发"]
category: ["blog", "前端"]
featured: true

---

基于 Ant Design 5 二次封装，打造更符合业务场景的 React 组件库 @digitalc/dxp-ui

## 前言
在现代前端开发中，组件库扮演着至关重要的角色，它能显著提升开发效率、保证 UI 一致性。Ant Design 无疑是国内 React 生态中最受欢迎的组件库之一。但在公司产品和项目开发中，我们常常需要针对具体的业务场景下， 进行组件库UI方面的调整或定制。所以决定对其进行二次封装，以更好地满足公司产品特定需求、统一团队产品的风格。

本文将介绍我们基于 Ant Design 5 打造的二次封装组件库`@digitalc/dxp-ui` 。探讨其设计理念、核心特性，特别是怎么样实现动态 Token 注入、处理 Ant Design v4/v5 兼容性问题，以及在开发过程中的一些思考和实践。

## 为什么需要二次封装？
Ant Design 提供了丰富的基础组件和强大的主题定制能力。但在大型项目或多业务线的场景下，直接使用 Ant Design 可能会遇到以下挑战：

1. 业务场景契合度 ：某些业务场景需要更特定、更复杂的组件交互或样式，直接使用基础组件可能需要编写大量重复的样式，导致代码冗余。
2. 设计规范统一 ：团队内部通常有统一的设计规范（Design System），需要将这些规范融入组件库，确保所有产品的视觉风格保持一致，提高用户体验和品牌感。
3. 主题管理复杂度 ：虽然 Ant Design 提供了 Token 定制，但在多主题（如不同品牌、不同产品线）切换和管理上，需要更便捷、更中心化、更快速、更简单的管理方式（领导想要的方式）。
4. 技术栈升级兼容 ：当项目需要在不同版本的 Ant Design（如 v4 和 v5）之间过渡或共存时，需要组件库层面提供良好的兼容性支持。
基于以上考虑，我们开始了`@digitalc/dxp-ui` 项目，旨在提供一套更贴合我们业务场景、易于维护和扩展的 React 组件库。

## @digitalc/dxp-ui 核心特性

`@digitalc/dxp-ui` 不仅仅是 Ant Design 的简单 token 包装，还包含了对业务需求痛点的深度思考和解决方案：

- 基于 Ant Design 5 ：享受 Ant Design 5 带来的性能提升、CSS-in-JS 支持和更灵活的 Token 系统。
- 业务场景组件 ：除了对基础组件进行样式和行为的定制，还封装了更贴合业务流程的复合组件（例如，在关联包`packages/business` 中规划）。
- 动态 Token 注入 ：这是`@digitalc/dxp-ui` 的核心亮点之一。我们设计了一套机制，允许在运行时动态注入自定义的 Token JSON 数据，轻松实现全局或局部主题的切换，满足一套产品，面对不同客户、品牌、项目的视觉需求。
- Ant Design v4/v5 兼容 ：考虑到存量项目,按功能模块逐个升级， 可能仍在会同时使用 Ant Design v4，我们提供了详细的兼容处理方案，使得`@digitalc/dxp-ui` 可以在 v4 项目中平稳运行。

## 技术实现细节

### 1. 动态注入自定义 Token JSON
Ant Design 5 的 Token 系统本身已经很强大了，但产品要求：希望实现更灵活的主题切换（虽然 Ant Design v5 官方提供了ConfigProvider机制，但并是很不适合我们，原因也在我们自己，因为 UI 设计前期是按客户需求定制，并且没有遵循antd的风格和规范做UI设计，是现有现有产品，后面才选择antd组件库，这样就导致我们的token 与antd token的映射关系不统一，无法直接粗暴的传入token即可改变主题）。为了解决这个问题，我们设计了`tokenManager` 模块实现了这一目标，它负责加载和应用自定义的 Token JSON 数据（ 并且做了与 antd token的值映射关系）。

```tsx
import { tokenManager } from '@digitalc/dxp-ui';

// 假设 customTokenJSON 是从 API 获取或本地加载的 Token 数据
const customTokenJSON = {
  colorPrimary: '#00b96b',
  colorLink: '#00b96b',
  // ... 其他 DXP 或 Ant Design Token
};

// 在应用初始化或需要切换主题时调用
tokenManager.loadExternalToken(customTokenJSON);
 ```

其内部实现原理大致如下：

- `tokenManager` : 维护一个全局的`tokenRef` 对象，存储当前的 Token 数据。`loadExternalToken` 方法会更新这个`tokenRef` 并触发一个自定义事件（如`xxx-token-updated` ）。
- `TokenContext` : 提供一个 React Context (`TokenContext` ) 和对应的 Provider (`GlobalTokenProvider` )。Provider 内部监听`xxx-token-updated` 事件，当事件触发时，更新 Context 的值（通常是一个版本号或时间戳）。
- `useDynamicTokens` Hook : 组件内部通过此 Hook 订阅`TokenContext` 。当 Context 值变化时，Hook 会重新执行，并调用`tokenManager` 中更新后的`getToken` 方法来获取最新的 Token 值。
- 组件应用 : 在组件（如`Button` ）的样式计算或`designTokens.ts` 中，使用`useDynamicTokens` 获取 Token 值，并将其传递给 Ant Design 的`ConfigProvider` 或直接应用于组件样式。
使得主题切换无需重新加载页面，实现了真正的动态响应。

```tsx
// designTokens.js
import { useDynamicTokens } from '@/utils';
/*
这是 dxp 的 UI token，缓存在本地的内置变量；
通过antd 提供的 ConfigProvider 注入了组件级 token 变量来实现 gomo 风格的UI组件；

理论上可以通过2种方式来实现 antd 的样式定制：
1. 直接写 /components/Button/style/button.less 文件通过 less 覆盖antd的样式，可控细节更多（相当于把  dxp 的 UI token 通过 less 的方式覆盖antd的样式）；
2. 通过 ConfigProvider 注入组件级别的 token 变量，这种不用写 less 文件，但是可控细节更少，只能antd 提供了哪些 token，才能覆盖对应的值；
目前优先选择第二种，因为第一种需要写 less 文件，要知道对应组件的dom结构，才能覆盖；而第二种只需要对齐 变量值，就能覆盖；
*/

const useDesignTokens = () => {
  const getToken = useDynamicTokens();
  return {
    // 将UI token 值，通过 useDynamicTokens 钩子获取，并映射给 antd 的 token
    colorText: getToken('colorStepperTextInactive'),
    colorTextDescription: getToken('colorStepperTextInactive'),
    colorTextLightSolid: getToken('colorStepperTextActive'),
  };
};

export { useDesignTokens };

 ```

然后在渲染组件中使用这个钩子，获取设计 token，并传递给组件，并且自定义了prefixCls，以实现组件样式的定制，并且不冲突antd本身，如果不够用，就要用 cssinjs的方案。

```tsx
import { designTokens } from './designTokens';

<ConfigProvider
prefixCls={cssClasses.PREFIX}
theme={{
  components: {
    Steps: {
      ...designTokens,
    },
  },
}}
>
<Steps
    {...props}
    prefixCls={prefixCls}
    style={{ ...otherDesignTokens, ...style }}
    className={className}
    items={processedItems}
    current={current}
    labelPlacement={labelPlacement}
  >
    {processedChildren}
  </Steps>
</ConfigProvider>
```
cssinjs的方案，可以参考antd的官方文档.

```tsx
import { useStyleRegister } from '@ant-design/cssinjs';
import { designTokens } from './designTokens';

  // 使用 useStyleRegister 注册自定义样式
  const useCustomToastStyle = () => {
    const {
      colorText,
      contentBg,
      contentPadding,
      borderRadiusLG,
    } = designTokens;

    const hashId = useStyleRegister(
      {
        theme: theme,
        token: {},
        path: [prefixCls + '-toast'],
      },
      () => `
      div[class*="-message"] .${prefixCls} div[class*="-message-notice-content"] {
        background-color: ${contentBg};
        color: ${colorText};
        border-radius: ${borderRadiusLG}px;
        padding: ${contentPadding};
      }
    `,
    );
    return hashId;
  };

  const hashId = useCustomToastStyle();

  // 返回 Toast 组件,并设置 hashId style
  return <Toast prefixCls={prefixCls} hashId={hashId} {...props} />;

```


### 2. Ant Design v4 和 v5 兼容性处理
在 Ant Design v4 项目中使用基于 v5 的`@digitalc/dxp-ui` 是一个常见的痛点。在`README.md` 中提供了详细的使用方案，核心思路是利用 npm alias 和 Ant Design v5 的`prefixCls` 特性：

1. 安装依赖别名 : 同时安装`antd@5` 和`antd@4` (使用别名如`antd4` )。
   ```json
   {
     "dependencies": {
       "antd": "^5.x.x",
       "antd4": "npm:antd@^4.x.x"
     }
   }
    ```

2. 配置构建工具 (以 Umi 3 脚手架为例) :
   - 关闭 Umi 对 antd 的默认处理 (`antd: false` )。
   - 可能需要配置`webpack-chain` 来处理`@digitalc/dxp-ui` 内部的 Less 文件编译（如果构建工具不支持自动处理 Less 时）。

3. 使用独立的`ConfigProvider` : 在应用根部或`@digitalc/dxp-ui` 组件外层包裹 Ant Design v5 的`ConfigProvider` ，并设置`prefixCls` (如`ant5` )，以隔离 v4 和 v5 的样式。
   ```tsx
   import { ConfigProvider as Antd5ConfigProvider } from 'antd';

   <Antd5ConfigProvider prefixCls="ant5">
     {/* 应用或 @digitalc/dxp-ui 组件 */}
   </Antd5ConfigProvider>
    ```
4. 按需引入 : 在代码中明确区分导入`antd` (v5) 和`antd4` 。
有效避免版本冲突和样式污染，实现 v4 和 v5 的和谐共存。

### 3. 整体流程与项目结构
`@digitalc/dxp-ui` 采用了 Monorepo 的结构（虽然当前示例只有一个`base components` 包），便于未来扩展业务组件库 (`business components` )。

- `packages/base` : 存放基础组件、工具函数和核心逻辑。
  - `src/components` : 各个基础组件的实现。
  - `src/utils` : 存放工具函数，如`tokenManager` ,`TokenContext` , 设备类型判断等。
  - `src/styles` : 全局样式或基础样式。
  - `.dumirc.ts` : dumi 的配置文件，用于生成组件文档和演示。
  - `.fatherrc.ts` : father 的配置文件，用于组件库的构建打包。
- `packages/business` (规划中) : 存放基于`base` 组件封装的业务组件。
开发流程遵循标准的 npm 组件库开发模式：

1. 组件开发 : 在`src/components` 中创建或修改组件，编写 TypeScript 代码和样式文件 (推荐使用 Less 并利用 Ant Design Token)。
2. Token 定义 : 在组件的`designTokens.ts` 文件中，使用`useDynamicTokens` 将设计规范映射到 Ant Design Token。
3. 文档编写 : 使用 Markdown 编写组件的 API 文档和使用示例 (`docs/demo` )。
4. 本地调试 : 运行 dumi (`npm start` ) 进行本地预览和调试。
5. 单元测试 : 编写 Jest 测试用例,确保组件功能正确。
6. 构建打包 : 运行 (`npm run build` ) 生成适用于不同环境（ESM, UMD, Lib）的产物。
7. 发布版本 : 使用 npm 发布到私有或公共仓库。
8. 发布文档 : 使用 dumi 构建并发布到 GitHub Pages 或其他静态网站托管平台，供用户查看和下载。vercel 就是个不错的方案。

## 简单小结
`@digitalc/dxp-ui` 是我们在 Ant Design 基础上，结合自身业务需求进行二次封装的一次成功实践。通过动态 Token 注入、精心的 v4/v5 兼容处理以及清晰的项目结构，我们构建了一个灵活、健壮且易于维护的组件库，理论上如果时间允许，建议还是纯自己开发，而不是使用第三方组件库是更好的方案，因为有一些dom结构，我们无法通过样式覆盖的方式来修改，只能通过js代码来修改，这样会增加开发成本和维护成本，目前也需要精心的v4/v5兼容处理和细心的Token注入处理差异点。

后续将继续完善迭代基础组件，并丰富基于组成组件拼装的业务组件库，持续优化开发体验和组件性能，使其更好地服务于我们的产品开发。

希望本文能对同样在进行组件库建设或 Ant Design 二次开发的同学有所启发。
