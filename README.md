## 小红书爆款文案生成器

一个基于 Node.js + Express + OpenAI 的小红书文案生成应用。填写类别、主题、语气、角色、侧重等信息，一键生成多版本可 A/B 测试的笔记文案。

### 快速开始

1) 安装依赖

```bash
npm install
```

2) 配置环境变量

复制 `.env.example` 为 `.env`，填入 `OPENAI_API_KEY`。

```
OPENAI_API_KEY=你的key
PORT=3000
```

3) 开发运行（热重载）

```bash
npm run dev
```

打开浏览器访问 `http://localhost:3000`。

4) 生产构建与运行

```bash
npm run build
npm start
```

### API

- POST `/api/generate`

请求体（部分字段可选）：

```json
{
  "category": "美妆",
  "topic": "油皮夏天如何稳住底妆？",
  "focusPoints": ["控油", "持妆"],
  "tone": "亲切",
  "persona": "资深护肤博主",
  "audience": "油皮、学生党",
  "structure": "引子-痛点-种草理由-使用体验-对比-拔草建议-结尾互动",
  "emojiLevel": 2,
  "hashtags": ["底妆", "油皮"],
  "bannedWords": ["绝对", "顶级"],
  "keyBenefits": ["清爽不油腻", "轻薄持妆"],
  "productInfo": "含有XX控油成分，SPF…",
  "scenarios": "夏日通勤",
  "ctaStyle": "温和",
  "wordRange": "200-400",
  "numVariants": 3,
  "model": "gpt-4o-mini",
  "temperature": 0.7
}
```

响应体：

```json
{
  "variants": [
    { "title": "…", "body": "…", "hashtags": ["#…"] }
  ],
  "warnings": ["…"],
  "meta": { "model": "gpt-4o-mini" }
}
```

### 提示词（Prompts）

- System Prompt: 见 `src/prompts/systemPrompt.ts`
- Assistant/User Prompt 模板：见 `src/prompts/assistantTemplate.ts`

更多设计细节见 `DESIGN.md`。


