# ASCII Generator

Author: Viet Nguyen <nhviet1009@gmail.com>  
Forked and maintained by Liu8Can <liucan01234@gmail.com>  
Repository: [https://github.com/Liu8Can/ASCII-generator](https://github.com/Liu8Can/ASCII-generator)

This project is licensed under the GPL-3.0 License.

[![License](https://img.shields.io/badge/license-GPLv3-blue)](https://opensource.org/licenses/GPL-3.0)
[![Python](https://img.shields.io/badge/python-3.6%2B-green)](https://www.python.org/)  
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-orange)](https://github.com/Liu8Can/ASCII-generator)  

## 📌 项目简介

这是一个基于 Python 的 ASCII 艺术生成工具，支持将图片和视频转换为 ASCII 艺术格式输出，支持灰度和彩色模式。以下是主要功能：
- **图片转换为文本 (txt)**  
- **图片转换为图片 (png, jpg)**  
- **视频转换为视频 (mp4, avi)**  
- 支持多种字符模式（简单/复杂）和背景选项（白底黑字/黑底白字）。  
- 支持彩色输出！  

---

## 🚧 项目问题与改进

### 原项目问题
1. **代码过时**：原项目使用了已废弃的 PIL 功能 `getsize`，导致代码无法运行。
2. **功能不完善**：原始代码生成的视频在右下角自动叠加原始视频，缺乏灵活性。
3. **兼容性问题**：部分库版本未明确，存在运行环境不一致的问题。
4. **文档不够详细**：对使用方法、参数含义解释不足。

### 改进内容
- **修复关键问题**：将过时的 `getsize` 替换为现代 PIL 功能 `getbbox`，使代码可正常运行。
- **优化视频功能**：去除右下角默认叠加原视频的设计，提升视频生成的自由度。运行`*_nodemo.py`文件的生成内容符合此要求。
- **代码结构优化**：增强代码的可读性和灵活性。
- **详细文档**：为用户提供详细的参数说明和使用指导，提升用户体验。

---

## 🌟 功能演示

### 多语言支持
生成不同语言的 ASCII 艺术，支持多种字母表（英语、日语、韩语等）。

| 示例 | 输出语言 |
|------|----------|
| ![English Output](demo/english_output.jpg) | 英语 |
| ![Japanese Output](demo/japanese_output.jpg) | 日语 |
| ![Chinese Output](demo/chinese_output.jpg) | 中文 |

### 视频转换
将视频转为复杂字符和彩色的动态 ASCII 视频输出：

| 示例 | 描述 |
|------|------|
| ![Colored Complex ASCII](demo/demo_complex_color_160.gif) | 彩色复杂字符输出 |
| ![White Background ASCII](demo/demo_simple_white_150.gif) | 白底简单字符输出 |

### 图片转换
将图片转为简单/复杂字符 ASCII 图片输出：

| 原始图片 | 简单字符 | 复杂字符 |
|----------|----------|----------|
| ![Input Image](demo/input.jpg) | ![Simple ASCII](demo/demo_image_simple.png) | ![Complex ASCII](demo/demo_image_complex.png) |

---

## 💻 使用方法

### 安装环境
1. 确保安装了 Python 3.6+。
2. 安装依赖库：
   ```bash
   pip install numpy opencv-python pillow
   ```


---

### 参数说明

**图片转换相关脚本（`img2img_color.py` 和 `img2img.py`）：**

| 参数           | 默认值         | 描述                                                         |
|----------------|----------------|--------------------------------------------------------------|
| `--input`      | `data/input.jpg` | 输入图片路径                                                 |
| `--output`     | `data/output.jpg` | 输出文件路径                                                 |
| `--language`   | `english`       | 使用的字符语言，例如 `english`、`japanese` 等               |
| `--mode`       | `standard`      | ASCII 字符模式（不同脚本可能支持不同模式，常用为 `standard`） |
| `--background` | `black`         | 背景颜色，可选值为 `black` 或 `white`                       |
| `--num_cols`   | `300`           | 输出 ASCII 图像的宽度（以字符数为单位）                      |
| `--scale`      | `2`（仅 `img2img_color.py`） | 缩放比例，仅适用于彩色输出脚本                               |

**视频转换相关脚本（`video2video_color.py` 和 `video2video.py`）：**

| 参数           | 默认值           | 描述                                                         |
|----------------|------------------|--------------------------------------------------------------|
| `--input`      | `data/input.mp4` | 输入视频路径                                                 |
| `--output`     | `data/output.mp4` | 输出视频路径                                                 |
| `--mode`       | `complex`（`video2video_color.py`），`simple`（`video2video.py`） | ASCII 字符模式，可选值为 `simple` 或 `complex`             |
| `--background` | `black`（`video2video_color.py`），`white`（`video2video.py`） | 背景颜色，可选值为 `black` 或 `white`                      |
| `--num_cols`   | `100`            | 输出 ASCII 视频的宽度（以字符数为单位）                      |
| `--scale`      | `1`              | 缩放比例                                                     |
| `--fps`        | `0`              | 输出视频帧率（默认为输入视频帧率）                           |
| `--overlay_ratio` | `0.2`         | 原始视频叠加比例（设置为 0 可完全移除叠加）                 |

---

### 使用示例

**图片转换示例：**
1. **图片转图片**（黑底，300字符宽度）：  
   ```bash
   python img2img.py --input data/input.jpg --output data/output.jpg --background black --num_cols 300
   ```
2. **图片转彩色图片**（白底，缩放2倍）：  
   ```bash
   python img2img_color.py --input data/input.jpg --output data/output.jpg --background white --scale 2
   ```

**视频转换示例：**
1. **视频转视频**（白底简单字符，移除叠加）：  
   ```bash
   python video2video.py --input data/input.mp4 --output data/output.mp4 --background white --overlay_ratio 0
   ```
2. **视频转彩色视频**（黑底复杂字符，帧率为30）：  
   ```bash
   python video2video_color.py --input data/input.mp4 --output data/output.mp4 --mode complex --fps 30
   ```

---


## 🔧 项目结构

```
ASCII-generator/
├── data/                      # 输入与输出的默认存储路径
├── demo/                      # 示例输出的演示文件（图片与GIF）
├── fonts/                     # 字符映射所需的字体文件
├── alphabets.py               # 多语言字符映射模块
├── img2img.py                 # 图片转图片ASCII脚本（单色）
├── img2img_color.py           # 图片转图片ASCII脚本（彩色）
├── img2txt.py                 # 图片转文本ASCII脚本
├── utils.py                   # 工具函数，包含核心算法逻辑
├── video2video.py             # 视频转视频ASCII脚本（单色）
├── video2video_color.py       # 视频转视频ASCII脚本（彩色）
├── video2video_nodemo.py      # 视频转视频ASCII脚本（右下角无原视频版本，提升效率）
├── video2video_color_nodemo.py # 视频转视频ASCII脚本（彩色，右下角无原视频版本）
├── LICENSE                    # 项目许可证
├── README.md                  # 项目说明文档
└── requirements.txt           # Python依赖项列表

```

---

## 📜 许可证

本项目采用 [GPLv3 许可证](LICENSE)。欢迎自由使用与二次开发。
您可以在 [GPLv3 官方网站](https://www.gnu.org/licenses/gpl-3.0.html) 查看完整协议条款。 
原有 MIT 许可协议内容适用于之前的版本。

---

**项目地址**  
- 原项目：[vietnh1009/ASCII-generator](https://github.com/vietnh1009/ASCII-generator)  
- 改进版项目：[Liu8Can/ASCII-generator](https://github.com/Liu8Can/ASCII-generator)  

让我们一起探索 ASCII 艺术的魅力吧！ ✨