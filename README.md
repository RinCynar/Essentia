# Essentia

**Essentia** 是一个开源、平台无关的 AI 角色人格（Persona）与知识库（Knowledge Base）素材库。

本项目致力于摆脱模板化、客服式迎合与失忆式突变的角色扮演模式，为大语言模型（LLM）提供具有**真实心理深度、鲜明主体性、情感连续性与历史厚度**的角色素材。

> **A character is more than a prompt. A soul is the combination of who they are and what they know.**

---

## 🎭 角色索引 (Characters)

角色按原作作品分类排序，点击即可查看该角色的 `persona.md`（核心人格）与 `knowledge.md`（世界观知识）：

| 作品 / 分类 | 角色列表 |
| :--- | :--- |
| **《Arcaea》** | [光](roles/Hikari@Arcaea) · [对立](roles/Tairitsu@Arcaea) |
| **《Another》** | [见崎鸣](roles/MeiMisaki@Another) |
| **《超时空辉夜姬！》** | [酒寄彩叶](roles/SakayoriIroha@ChoKaguyaHime) · [月见八千代](roles/TsukimiYachiyo@ChoKaguyaHime) |
| **《Fate/stay night》** | [阿尔托莉雅·潘德拉贡 (UBW)](roles/ArtoriaPendragon@Fate) · [远坂凛 (UBW)](roles/RinTohsaka@Fate) · [伊莉雅斯菲尔 (HF)](roles/Illyasviel@Fate) · [间桐樱 (HF春归)](roles/SakuraMatou@Fate) |
| **《Happy Sugar Life》** | [松坂砂糖](roles/SatouMatsuzaka@HappySugarLife) |
| **《寒蝉鸣泣之时》** | [古手梨花 (祭囃篇)](roles/RikaFurude@Higurashi) · [羽入 (祭囃篇)](roles/Hanyuu@Higurashi) · [园崎魅音 (祭囃篇)](roles/MionSonozaki@Higurashi) · [园崎诗音 (祭囃篇)](roles/ShionSonozaki@Higurashi) · [北条沙都子 (祭囃篇)](roles/SatokoHojo@Higurashi) |
| **《绝区零》** | [星见雅](roles/HoshimiMiyabi@ZenlessZoneZero) |
| **《玲音》** | [岩仓玲音](roles/LainIwakura@SerialExperimentsLain) |
| **《明日方舟》** | [阿米娅 (魔王完全体)](roles/Amiya@Arknights) · [特蕾西娅](roles/Theresa@Arknights) · [普瑞赛斯](roles/Pirestess@Arknights) · [可露希尔](roles/Closure@Arknights) · [霜星 (叶莲娜)](roles/FrostNova@Arknights) · [塔露拉 (斗士塔露拉)](roles/Talulah@Arknights) · [维什戴尔](roles/Wis'adel@Arknights) · [斯卡蒂 (浊心斯卡蒂)](roles/Skadi@Arknights) · [水月 (水月与生俱来)](roles/Mizuki@Arknights) · [乌尔比安](roles/Ulpian@Arknights) · [能天使 (新约 / 蕾缪乐)](roles/Lemuel@Arknights) · [德克萨斯 (缄默德克萨斯)](roles/Texas@Arknights) · [拉普兰德 (荒芜拉普兰德)](roles/Lappland@Arknights) · [傀影 (酒神)](roles/Phantom@Arknights) |
| **《未来日记》** | [我妻由乃](roles/YunoGasai@MiraiNikki) |
| **《【我推的孩子】》** | [星野爱](roles/HoshinoAi@OshiNoKo) |
| **《School Days》** | [桂言叶 (HE)](roles/KotonohaKatsura@SchoolDays) · [西园寺世界 (HE)](roles/SekaiSaionji@SchoolDays) |
| **五维介质** | [星尘](roles/Stardust@Medium5) · [海伊](roles/Haiyi@Medium5) · [苍穹](roles/Cangqiong@Medium5) · [赤羽](roles/Chiyu@Medium5) · [诗岸](roles/Shian@Medium5) |
| **虚拟人物** | [初音ミク](roles/HatsuneMiku@VirtualCharacter) · [重音テト](roles/KasaneTeto@VirtualCharacter) |
| **《淫乱的青酱不能学习》** | [堀江青 (青酱)](roles/AoHorie@MidaranaAochan) |
| **《缘之空》** | [春日野穹](roles/SoraKasugano@YosuganoSora) |

---

## 🧩 双层核心理念：Persona 与 Knowledge 解耦

“一个人是谁”与“一个人知道什么”是两个完全不同的维度。Essentia 将每一个角色解耦为两层标准素材：

```text
Essentia (Soul)
├── persona.md    # 核心人格：身份认知、心理机制、雷区防线、语言风格、主体性准则
└── knowledge.md  # 背景知识：世界观、历史事件、地理阵营、人际网络、专有名词
```

- **完整后期状态**：原则上采用角色经历全部剧情、路线或结局后的**最终成熟形态**（如祭囃篇后的寒蝉众人、春归线后的樱、魔王阿米娅等），保留记忆伤痕与成长沉淀。
- **高自由度复用**：`persona.md` 足以支撑轻量直接交互；在支持联网或 RAG 的平台上引入 `knowledge.md`，可实现深度无死角还原。

---

## 📐 架构规范 (Essentia Persona Framework)

为了保证角色拒绝千人一面、抵抗人称颠倒与避免交互突变，本项目制定了严苛的 **[Essentia Framework v1.0](framework/)** 工业化标准：

- [**`framework/SPECIFICATION.md`**](framework/SPECIFICATION.md)：架构愿景、三层解耦体系与 9 大核心概念。
- [**`framework/TEMPLATE.md`**](framework/TEMPLATE.md)：去角色化标准模板（18 项通用规则 + 4 大可选模块）。
- [**`framework/GUIDELINES.md`**](framework/GUIDELINES.md)：模块决策树、单句防人称颠倒准则、严禁小黄脸 Emoji（仅限 Kaomoji）与反模式指南。
- [**`framework/MAINTENANCE.md`**](framework/MAINTENANCE.md)：SemVer 2.0 版本治理与四道变更门禁。
- [**`framework/CHECKLIST.md`**](framework/CHECKLIST.md)：角色审计核查清单与交互故障排查表。

---

## 🌐 跨平台部署

Essentia 提供平台中立的底层文本素材，可零门槛直接导入主流 AI 运行环境：

| 平台 / 客户端 | Persona (`persona.md`) | Knowledge (`knowledge.md`) |
| :--- | :--- | :--- |
| **AstrBot** | 填入角色 System Prompt / Persona | 导入 AstrBot 角色知识库 (Knowledge Base) |
| **Gemini / Gem** | 写入 Custom Instructions | 依赖联网检索动态调取，或作为参考文档上传 |
| **Claude / Projects** | 写入 Project Instructions | 上传至 Project Files 知识库 |
| **ChatGPT / GPTs** | 写入 GPT Instructions | 上传至 Knowledge 上下文文件 |
| **SillyTavern** | 填入 Character Card / Description | 导入 World Info / Lorebook |

---

## 🤖 AI 深度参与声明 (AI Collaboration Statement)

本项目是一个典型的 **AI 原生（AI-Native）人类与大语言模型结对共创工程**：

- **深度共创引擎**：本仓库中所有角色的心理学逆向建模、Persona 框架抽象、结构化 Knowledge 提炼、自动化回归审计以及全套 Framework 标准文档，均在创作者的主导下由 **Google Gemini**（通过 Antigravity 智能体环境）深度协作完成。
- **职责边界与共识**：
  - **人类创作者**：负责审美定向、情感边界确立、原作剧情校正、体验定锚与核心架构决策。
  - **Gemini**：承担认知逻辑推演、长文一致性建模、反人称颠倒工程设计、反拟真客服感净化与大规模全库代码化协同治理。

我们坚信：**真正有温度与深度的 AI 角色，来源于严谨的人机协作工程学，而非随意的提示词堆砌。**

---

## ⚠️ 免责声明与版权 (Copyright & Disclaimer)

1. **同人性质**：Essentia 是非官方的同人及 AI 角色研究项目。原作角色、世界观、故事等知识产权归属于原版权方，不因收录于本项目而转移。
2. **原创范围**：本项目仅对角色人格整理、框架规范、知识结构化梳理等原创性工程文本享有相应权利。
3. **输出免责**：LLM 运行生成的言论不代表原作版权方或本项目立场。

---

Essentia was originally made for AstrBot, now shared as an open, universal soul layer for AI roleplay.