# Create-react-app

CRA（Create React App）是一个由 Facebook 创建的脚手架工具，用于快速搭建 React 应用程序的基本项目结构和开发环境。CRA 提供了一个零配置的开发环境，使得新手开发者能够快速上手 React 开发，而无需担心复杂的配置。

#### 处理内置配置

使用 CRA 创建项目时，项目的配置文件和脚本都是隐藏的，因此如果想要处理这些配置，需要用到以下几种方法：

* eject
* 通过 CRA 官方支持的 --scripts-version 参数，创建项目时使用自己重写过的 react-scripts 包
* 使用 react-app-rewired + customize-cra 组合覆盖配置
* 使用 craco 覆盖配置

#### eject 命令

使用 eject 后项目将完全由自己管理，但这是一个不可逆的过程，弹出配置后，将无法跟随官方的脚步去升级项目的 react-script 版本。

#### CRACO

一个第三方库，CRACO 即 Create React App Configuration Override，意思是重写配置，可以在不 eject 的情况下管理配置。

#### 单页应用

Create React App 默认生成的项目是单页应用（SPA）。生成的项目结构通常只包含一个 HTML 文件（`public/index.html`），其中包含一个根节点（root）用于挂载 React 应用的组件。React 应用的所有页面切换都是在该单个 HTML 文件中进行的，通过 React Router 等方式实现前端路由和组件的动态更新。

\
\## 待学习

虽然 Create React App 默认生成的项目是单页应用，但你可以根据需要进行修改和自定义，使其支持多页应用。你可以自行添加其他 HTML 文件，并为每个页面创建独立的组件和路由逻辑。然后，你可以使用 Webpack 或其他构建工具来配置多入口点（entry points）和输出（output），实现多个独立页面的构建。
