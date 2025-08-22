> agent 交互 GUI，robot 操作实体世界。  
> 是时候打通了。  
> **TaskFlow** —— 使用类似markdown、latex的自然语言来描述一个的动作序列，容易被 LLM 理解、生成以驱动agent操作。最终形态可能类似目前ai的联网搜索开关，打开以后他可以按时间序列操作你的窗口，虽然目前还没想好 看的部分，多模态理解怎么实现。

---

## 📦 TaskFlow 仓库速览
```
task-flow/
├── README.md
├── examples/
│   ├── agent-gui.taf      # LLM 点击浏览器
│   ├── robot-pick.taf     # 机械臂抓方块
│   └── vr-hand.taf        # VR 手势动作
├── parser/                # Python & JS 零依赖
├── spec/                  # 语法白皮书
└── LICENSE
```

---

## 🚀 30 秒上手
1. **写动作**  
   `agent-gui.taf`  
   ```taf
   #coord screen px ms
   [0] click @ (120 340) target=login-btn
   [150] drag @ (120 340)(400 340)
   [450] release @ (400 340)
   ```

2. **一句话重放**  
   ```bash
   pip install taskflow
   taskflow replay agent-gui.taf --backend webdriver
   ```
   同一文件还能换成 `--backend ros` 直接驱动机械臂。

---

## ✏️ 语法速写
| 元素 | 示例 | 说明 |
|---|---|---|
| 帧头 | `#coord screen px ms` | 坐标系 + 单位 |
| 时间戳 | `[0]` `[150]` | 毫秒或帧 |
| 动作 | `click` `grab` `move` | 动词即动作 |
| 坐标 | `(120 340)` 或 `(x y z)` | 无逗号 |
| 路径 | `(x1 y1)(x2 y2)` | 关键帧串 |
| 元数据 | `target=button1` `hand=right` | 任意键值 |

---

## 🌐 场景一行切换
- **GUI Agent** `#coord screen px ms`  
- **机器人** `#coord robot mm s`  
- **VR/AR** `#coord vr m ms`  

---

## 📁 文件格式
`.taf` = **Task Action Flow**  
已提交 IANA 预申请，零冲突。

---

## 🧩 生态
- **VS Code 高亮** [marketplace](https://marketplace.visualstudio.com/items?itemName=taskflow.taf)  
- **Web 播放器** [demo](https://taskflow.dev/play)  
- **Unity / ROS / WebXR** 插件 PR 欢迎！

---

## 📄 License
MIT © TaskFlow Contributors

> 把动作写成文本，让 agent 与 robot 说同一种语言。
