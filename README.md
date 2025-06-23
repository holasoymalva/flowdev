# 🧠 FLOWDEV — Automate Developer Tasks with AI Prompts

What if you could just **type a prompt** and FLOWDEV did the boring dev work for you?

Refactor code. Generate unit tests. Add logging. Scaffold API endpoints. All from one CLI + VSCode plugin — powered by GPT-4.

FLOWDEV turns your prompt into production-ready code, directly in your repo.  
It’s like having a senior dev on standby, 24/7.

---

## ⚡ Features

- 🔁 **Refactor your code** via prompt  
  → `flowdev "Refactor this controller to clean architecture"`

- 🧪 **Generate unit tests**  
  → `flowdev "Write Jest tests for this service"`

- 🧰 **Add logging** (Pino, Winston, etc.)  
  → `flowdev "Add logging to these API handlers"`

- 🔒 **Add input validation**  
  → `flowdev "Add Zod validation to this endpoint"`

- 📄 **Generate documentation**  
  → `flowdev "Generate Swagger docs for this file"`

- 🧠 Works with:
  - JavaScript / TypeScript
  - Angular, React, Node.js
  - More coming soon...

---

## 🚀 Quick Start

### 1. Install the CLI

```bash
npm install -g flowdev
````

### 2. Authenticate

```bash
flowdev auth
```

> Requires an OpenAI API Key or Gemini API Key.

### 3. Run on your code

```bash
flowdev "Write unit tests for this file" --file src/api/user.ts
```

You can also pipe code directly:

```bash
cat service.ts | flowdev "Refactor this to use dependency injection"
```

Or use with Git staged files:

```bash
git diff --cached | flowdev "Add comments and logs"
```

---

## 🧩 Integrations

* ✅ VS Code Extension (optional)
* ✅ GitHub Actions (coming soon)
* ✅ Git pre-commit hook (`.flowdevrc`)
* ✅ Output to file or terminal
* ✅ Custom prompt templates

---

## 💡 Use Cases

| Prompt                                           | What it does                           |
| ------------------------------------------------ | -------------------------------------- |
| `"Add logging to all routes"`                    | Adds `logger.info()` or Pino to routes |
| `"Generate Swagger for this controller"`         | Generates OpenAPI spec                 |
| `"Write tests"`                                  | Creates Jest or Vitest test file       |
| `"Explain this regex"`                           | Outputs a plain-English explanation    |
| `"Translate this Angular service to React hook"` | Converts Angular logic to React        |

---

## 🔐 Security

* Code never leaves your local machine unless explicitly allowed.
* Supports local models (coming soon).
* Add `.flowdevignore` to skip sensitive files.

---

## 🛠️ Roadmap

* [ ] GitHub PR suggestions
* [ ] GPT-based code review
* [ ] Custom model support (Claude, Mistral, etc.)
* [ ] Local inference mode (Ollama)

---

## 👨‍💻 Created by Developers, for Developers

FLOWDEV was built by devs tired of repetitive tasks and long refactor sessions.
If you live in TypeScript, CLI tools, and unit tests — this is for you.

---

## 📫 Join the Dev Beta

Get early access, report issues, or request features:

* [x] GitHub Issues
* [x] Discord Community (coming soon)
* [x] Twitter: [@flowdev\_ai](https://twitter.com/flowdev_ai)
* [x] Site: [flowdev.tools](https://flowdev.tools)

---

## 🧪 Sample Prompt

```bash
flowdev "Add Zod validation to this route handler" --file routes/user.ts
```

Before:

```ts
app.post("/user", async (req, res) => {
  const user = req.body;
  saveUser(user);
});
```

After:

```ts
import { z } from "zod";

const UserSchema = z.object({
  name: z.string(),
  email: z.string().email(),
});

app.post("/user", async (req, res) => {
  const parseResult = UserSchema.safeParse(req.body);
  if (!parseResult.success) return res.status(400).json(parseResult.error);
  saveUser(parseResult.data);
});
```

---

## 📄 License

MIT License © 2025 — [@holasoymalva](https://github.com/holasoymalva)
