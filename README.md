# 小知 · 圆胖猫头鹰

一只圆滚滚的棕色小猫头鹰：大金色眼睛、短翅膀、小脚爪。
造型参考选定的 Pigwidgeon（小猪）Q 版概念，使用内置 imagegen 制作。

![小知歪头](previews/waiting.gif)

## 文件

| 路径 | 内容 |
| --- | --- |
| [assets/spritesheet.png](assets/spritesheet.png) | 最终透明精灵图，用于宠物客户端接入 |
| [pet.json](pet.json) | 布局、动作帧数、时间和视线方向 |
| [previews/all-states.gif](previews/all-states.gif) | 九种动作总览 |
| [previews/all-states.mp4](previews/all-states.mp4) | 视频预览 |
| [previews/look-loop.gif](previews/look-loop.gif) | 十六个视线方向 |
| [previews/idle-jump-idle.gif](previews/idle-jump-idle.gif) | 待机与跳跃衔接 |
| [source/](source/) | 当前有效主体、动作条、参考图和布局参考 |
| [prompts/](prompts/) | 实际使用的生成提示词，包含跳跃修订记录 |
| [qa/](qa/) | 最终检查图和校验记录 |
| [SHA256SUMS](SHA256SUMS) | 仓库素材的完整性校验值 |

## 精灵图布局

- Pets v2，透明 PNG，1536 × 2288 像素。
- 8 列 × 11 行，每格 192 × 208 像素。
- 前九行动作帧数依次为：6、8、8、4、5、8、6、6、6。
- 最后两行是十六个顺时针视线方向；0° 向上，90° 向右。
- 普通待机使用 `idle`；`running` 表示专注处理，左右移动使用拍翅动作。

| 行（从 0 开始） | 状态 | 帧数 |
| --- | --- | --- |
| 0 | 待机 idle | 6 |
| 1 | 向右移动 running-right | 8 |
| 2 | 向左移动 running-left | 8 |
| 3 | 挥翅 waving | 4 |
| 4 | 小跳 jumping | 5 |
| 5 | 受挫 failed | 8 |
| 6 | 等待 waiting | 6 |
| 7 | 思考 running | 6 |
| 8 | 检查 review | 6 |
| 9–10 | 视线方向 | 16 |

## 检查记录

2026-11-08 制作时，最终文件通过精灵图结构、透明背景、边缘清理、动作几何检查和 Pets 预检。
四个基本视线方向通过独立盲审；少量中间方向的单轴偏移较细微，记录在 `qa/` 的警告中。
源图中的洋红色背景用于抠图，最终 `assets/spritesheet.png` 使用透明背景。

提示词是制作时的记录。`source/references/` 包含当时使用的参考素材，其中旧版白色雪鸮只作为动作参考。
仓库中的校验报告副本已将本机绝对路径改成相对路径，精灵图字节保持不变。

素材完整性检查（macOS / Linux）：

```sh
shasum -a 256 -c SHA256SUMS
```
