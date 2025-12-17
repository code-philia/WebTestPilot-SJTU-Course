# WebTestPilot

<a href="./README.md">English</a> •
<a href="./README.zhcn.md">简体中文 (Simplified Chinese)</a>

WebTestPilot 是一个基于大语言模型（LLM）的自动化网页测试工具。

本版本基于原始工具修改，专门用于上海交通大学（SJTU）课程教学。

## 环境准备

在开始之前，请确保你已经安装 `uv` 包管理器。（[安装指南](https://docs.astral.sh/uv/getting-started/installation/)）

## 安装指南

1. **克隆代码仓库**

2. **安装 WebTestPilot PyTest 插件**

    ```bash
    # 安装所有项目依赖
    uv sync
    ```

3. **配置环境变量**

    我们使用 `.env` 文件来存放配置项和密钥（例如 API Key）。

    复制模板文件，修改内容：

    ```bash
    cp .env.example .env
    ```

## 使用指南

1. **启动 Chrome 浏览器**

    WebTestPilot 不会每次都新开浏览器，而是连接到一个已经运行的 Chrome 实例。

    根据你的操作系统运行：

    ```bash
    # macOS / Linux / WSL
    source ./browsers/browser.sh
    ```

    ```powershell
    # Windows
    powershell -ExecutionPolicy Bypass -File ./browsers/browser.ps1
    ```

    这会启动一个带特殊配置的 Chrome 浏览器，供 WebTestPilot 控制。

2. **手动登录（只需一次）**

    在打开的 Chrome 中访问你要测试的网站，手动登录账号。登录状态会被保存在浏览器配置中，后续测试会自动复用。

    *请不要关闭浏览器*，否则需要重新登录。

3. **使用 Pytest 运行测试**

    运行以下命令：

    ```bash
    uv run pytest [测试文件或文件夹路径] -v --url [测试网站 URL]
    # 示例
    uv run pytest ./tests/12306/dining-view-merchant-details.json -v --url https://www.12306.cn
    ```