# NS 游戏 Apple ARM 原生移植 Skill

面向 AI 编程助手的指令型 skill，用于将 Nintendo Switch 游戏适配到 Apple Silicon macOS、iPadOS 和 iOS。以 Rust 原生兼容层与 Metal 为核心，覆盖版本识别、AArch64 离线改写、Horizon 服务、NVN → Metal、输入音频、部署及实机验收。

## 安装与使用

将仓库克隆到助手的 skills 目录。例如安装到 Codex：

```bash
git clone https://github.com/realskyrin/ns-game-apple-arm-port.git ~/.codex/skills/ns-game-apple-arm-port
```

重新加载助手后，在目标游戏移植项目中使用：

```text
使用 $ns-game-apple-arm-port 检查当前游戏版本和移植基础，按 Rust 与 Metal 架构先集中完成当前目标内的全量代码修改，再统一测试、集中修复与定向复测，并记录实际运行证据与未验证项。
```

也可以直接让助手读取 [SKILL.md](SKILL.md)。目标仓库、资源位置与设备由具体任务提供。

## 默认工作节奏

1. 盘点当前目标的已知缺口和依赖，连续完成跨模块实现、调用方与平台配置。
2. 修改完成后统一检查、构建、测试和游戏验收，汇总失败；实现期间不逐文件或逐补丁启动测试。
3. 按根因集中修复，定向复测失败项和受影响项，再用最终构建确认受影响的游戏路径。

只有缺失关键事实、后续实现无法可靠继续时，才提前执行最小探针。全量修改以当前任务为边界，最终仍需真实运行证据，不将代码完成或构建成功等同于可玩。

## 内容

- [SKILL.md](SKILL.md)：工作流程、语言架构、诊断与交付要求。
- [架构与推进](references/architecture-and-workflow.md)：Rust 模块边界、版本适配与最短验证路径。
- [执行层与平台](references/runtime-and-platforms.md)：装载、ABI、服务、线程、平台部署与音频。
- [图形与排障](references/graphics-and-debugging.md)：NVN → Metal、纹理一致性、shader 与性能诊断。
- [验收与案例](references/validation-and-cases.md)：证据阶梯、记录模板与可迁移经验。
- [Codex 元数据](agents/openai.yaml)：名称、简介与默认提示词。

本仓库提供移植方法与诊断指导，不包含游戏、密钥、固件、兼容层实现或构建产物。游戏资源保持本地；仅交付有权分发的内容。构建、启动、画面、输入、音频与可玩性分别以实际证据验收。

## 致谢与参考

本 Skill 将本地游戏移植实践整理为通用工作方法。感谢以下项目公开原生执行、兼容层和平台适配的设计与实现；其中经验来源与相关工程参考分别说明如下：

- **[c22dev/mush8](https://github.com/c22dev/mush8)**：本 Skill 的 Rust/Cargo 模块划分提炼自基于 mush8 的本地 BOTW 移植实践。mush8 的 ARM64 离线改写、Horizon 宿主、NVN → Metal，以及 macOS 运行时装载与 iOS 构建期链接的分工，是相关架构经验的来源。
- **[jhaizhou-ops/d2r-mobile](https://github.com/jhaizhou-ops/d2r-mobile)**：本 Skill 所总结的早期 iPad 移植实践曾参考其原游戏 ARM64 代码改写、宿主服务、离线 shader 转换与 iOS 壳层路线；跨游戏复用的是方法与边界，游戏专用地址、补丁和逻辑仍需独立核实。
- **[ly05010419/MacNativeGames](https://github.com/ly05010419/MacNativeGames)**：作为相关工程参考，展示了用户自备资源、按版本核验模块、原生执行与 Metal 图形适配、独立缓存/存档，以及区分构建检查和真实游戏验收的实践。它与本 Skill 的路线相呼应；当前未确认它是本 Skill 原始编写时的直接来源。

以上致谢说明思路与实践的关联，不表示这些项目为本 Skill 背书，也不表示本仓库包含其运行时代码。

## 许可证

本仓库的原创 Skill 指令、文档与元数据采用 [MIT License](LICENSE)。

参考项目及其代码仍遵循各自许可证：mush8 为 GPL v3，d2r-mobile 与 MacNativeGames 为 MIT；其中第三方组件以各项目的许可声明为准。本仓库的 MIT 许可不覆盖这些外部代码或任何游戏程序、资源、密钥及固件。
