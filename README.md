# SimsTalk

SimsTalk 是一个为《模拟人生4》(The Sims 4) 游戏打造的 AI 对话增强工具，通过 Socket 通信与游戏 Mod 配合，实现游戏角色之间的智能对话生成。

## 功能特性

- **AI 对话生成**：基于大语言模型生成游戏角色之间的自然对话
- **Socket 服务器**：稳定的本地 Socket 通信，支持与游戏 Mod 实时数据交互
- **Jinja2 提示词模板**：支持自定义提示词模板，灵活配置对话生成逻辑
- **记忆系统**：自动记录对话历史，支持角色记忆功能
- **游戏内对话框**：可拖动的透明对话框叠加层，支持自定义样式
- **Mod 管理**：自动检测、安装和更新游戏 Mod
- **版本检查**：优先从 GitHub 获取版本，Gitee 作为备用源

## 技术栈

- Python 3.8+
- Tkinter / ttkbootstrap (GUI)
- Jinja2 (模板引擎)
- Socket (网络通信)
- Requests (HTTP 请求)

## 快速开始

### 环境要求

- Python 3.8 或更高版本
- 《模拟人生4》游戏（需安装对应 Mod）

### 安装步骤

1. **克隆项目**

```bash
git clone https://github.com/xczEndsub/SimsTalk-mod.git
cd SimsTalk
```

2. **安装依赖**

```bash
pip install -r requirements.txt
```

3. **运行应用**

```bash
python SimsTalkApp/SimsInfoClient.py
```

## 配置说明

### 基础设置

| 设置项 | 说明 | 默认值 |
| :--- | :--- | :--- |
| Mods 文件夹 | 游戏 Mods 目录路径 | `Documents/Electronic Arts/The Sims 4/Mods` |
| Socket 端口 | 通信端口号 | 21908 |
| 字号大小 | 对话框字体大小 | 20 |
| 透明度 | 对话框透明度 (0-1) | 0.9 |
| 文字颜色 | 对话框文字颜色 | #0066ff |
| 自动隐藏 | 是否自动隐藏对话框 | True |
| 隐藏延迟 | 自动隐藏延迟时间（秒） | 5 |
| 对话间隔 | 对话显示间隔（秒） | 3 |

### 模型配置

支持配置大语言模型参数：
- Model Provider: OpenAI 或自定义
- API Base 地址
- API Key
- Max Tokens
- Temperature

## 使用指南

### 启动流程

1. 运行 SimsTalk 应用
2. 配置 Mods 路径（可自动检测）
3. 安装/更新 SimsTalk Mod
4. 配置 AI 模型参数
5. 启动游戏，应用自动连接

### 对话框操作

- **拖动**：点击对话框顶部区域拖动位置
- **自动隐藏**：鼠标离开对话框后自动隐藏
- **滚动**：文本过长时自动显示滚动条

### 提示词模板

应用使用 Jinja2 模板引擎，支持以下变量：

| 变量 | 说明 | 示例 |
| :--- | :--- | :--- |
| `sims_data` | 角色数据列表 | `sims_data[0].name`, `sims_data[0].mood` |
| `time` | 当前时间 | "9:31 周日" |
| `location` | 当前地点 | "客厅" |
| `weather` | 天气 | "晴天" |
| `season` | 季节 | "夏季" |
| `atmosphere` | 对话氛围 | "随意" |
| `memory` | 角色记忆 | 历史对话记录 |

## 项目结构

```
SimsTalk/
├── SimsTalkApp/
│   ├── SimsInfoClient.py    # 主应用程序
│   ├── simstalk_config.json # 配置文件
│   ├── prompt_presets/      # 提示词预设目录
│   │   └── default.json     # 默认提示词模板
│   └── SimsTalk.png         # 应用图标
├── SimsTalk.py              # 游戏 Mod 代码
├── requirements.txt         # 依赖列表
└── README.md                # 项目说明
```

## Mod 安装

应用会自动检测 Mod 安装状态，点击"安装 Mod"或"更新 Mod"按钮即可自动下载安装。

Mod 文件会下载到以下目录：
```
Mods/SimsTalk/
├── SimsTalk.package
└── SimsTalk.ts4script
```

## 版本检查机制

应用采用双源版本检查策略：
1. **优先**从 GitHub 获取最新版本
2. **备用**从 Gitee 获取（适用于网络受限环境）

## 常见问题

### 端口被占用

如果提示"端口被占用"，请在设置中修改 Socket 端口号，选择一个未被占用的端口（如 21909）。

### 连接失败

1. 确保游戏已启动且 Mod 已正确加载
2. 检查防火墙设置，允许应用通信
3. 确认端口号配置一致

### 对话框不显示

1. 确保游戏窗口处于活动状态
2. 检查对话框透明度设置
3. 尝试调整对话框位置

## 许可证

MIT License

## 贡献

欢迎提交 Issue 和 Pull Request！

## 联系方式

如有问题或建议，请通过以下方式联系：
- GitHub: https://github.com/xczEndsub/SimsTalk-mod
- Gitee: https://gitee.com/xczend/sims-talk_-mod