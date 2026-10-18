# NS 游戏 Apple ARM 原生移植 Skill

面向 AI 编程助手的指令型 skill，用于将 Nintendo Switch 游戏适配到 Apple Silicon macOS、iPadOS 和 iOS。以 Rust 原生兼容层与 Metal 为核心，覆盖版本识别、AArch64 离线改写、Horizon 服务、NVN → Metal、输入音频、部署及实机验收。

## 安装与使用

将仓库克隆到助手的 skills 目录。例如安装到 Codex：

```bash
git clone https://github.com/realskyrin/ns-game-apple-arm-port.git ~/.codex/skills/ns-game-apple-arm-port
```

私有仓库需要先配置 GitHub Git 访问权限。重新加载助手后，在目标游戏移植项目中使用：

```text
使用 $ns-game-apple-arm-port 检查当前游戏版本和移植基础，按 Rust 与 Metal 架构推进，并记录实际运行证据与未验证项。
```

也可以直接让助手读取 [SKILL.md](SKILL.md)。目标仓库、资源位置与设备由具体任务提供。

## 已经移植的启动器下载
https://pan.baidu.com/s/1HwTlxwHJd8bUfCenBIxcHg?pwd=ttwi 

## 内容

- [SKILL.md](SKILL.md)：工作流程、语言架构、诊断与交付要求。
- [架构与推进](references/architecture-and-workflow.md)：Rust 模块边界、版本适配与最短验证路径。
- [执行层与平台](references/runtime-and-platforms.md)：装载、ABI、服务、线程、平台部署与音频。
- [图形与排障](references/graphics-and-debugging.md)：NVN → Metal、纹理一致性、shader 与性能诊断。
- [验收与案例](references/validation-and-cases.md)：证据阶梯、记录模板与可迁移经验。
- [Codex 元数据](agents/openai.yaml)：名称、简介与默认提示词。

本仓库提供移植方法与诊断指导，不包含游戏、密钥、固件、兼容层实现或构建产物。游戏资源保持本地；仅交付有权分发的内容。构建、启动、画面、输入、音频与可玩性分别以实际证据验收。
