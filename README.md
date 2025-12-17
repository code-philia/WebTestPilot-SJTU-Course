# WebTestPilot

<a href="./README.md">English</a> •
<a href="./README.zhcn.md">简体中文 (Simplified Chinese)</a>

WebTestPilot is an LLM-driven automated web testing framework for end-to-end browser testing.

This version is specifically intended for course teaching at Shanghai Jiao Tong University (SJTU).

## Prerequisites

Before getting started, please make sure you have installed the uv package manager. ([Guide](https://docs.astral.sh/uv/getting-started/installation/))

## Installation

1. **Clone the code repository**

2. **Install the WebTestPilot PyTest plugin**

    ```bash
    # Install all project dependencies
    uv sync
    ```

3. **Configure environment variables**

    We use a `.env` file to store configuration options and secrets (such as API keys).

    Copy the template file and modify it as needed:

    ```bash
    cp .env.example .env
    ```

## Usage

1. **Start the Chrome browser**

    WebTestPilot does not launch a new browser each time. Instead, it connects to an already running Chrome instance.

    Run the following command based on your operating system:

    根据你的操作系统运行：

    ```bash
    # macOS / Linux / WSL
    source ./browsers/browser.sh
    ```

    ```powershell
    # Windows
    powershell -ExecutionPolicy Bypass -File ./browsers/browser.ps1
    ```

    This will start a Chrome browser with special configurations that WebTestPilot can control.

2. **Manual login (only required once)**

    In the opened Chrome browser, visit the website you want to test and log in manually. The login state will be saved in the browser profile and automatically reused in subsequent tests.

    *Please do not close the browser*, otherwise you will need to log in again.

3. **Run tests with Pytest**

    Run the following command:

    ```bash
    uv run pytest [test file or directory path] -v --url [target website URL]
    # Example
    uv run pytest ./tests/12306/dining-view-merchant-details.json -v --url https://www.12306.cn
    ```