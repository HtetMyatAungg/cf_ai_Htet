# CF Code Reviewer

An AI-powered code review API built on Cloudflare Workers, using Workers AI (Llama 3.1) to provide intelligent code analysis at the edge.

**Live API:** https://cf-code-reviewer.jianghenry25.workers.dev

## Features

- **`POST /review`** — Analyses code for bugs, best practices, performance issues, and security vulnerabilities. Returns a quality rating (1-10).
- **`POST /explain`** — Explains code in plain English for beginners.
- **`POST /suggest`** — Provides specific refactoring suggestions with improved code snippets.
- **`GET /`** — Returns API documentation as JSON.

## Tech Stack

- **Cloudflare Workers** — Serverless compute at the edge (330+ cities globally)
- **Workers AI** — Runs Meta Llama 3.1 8B Instruct model on Cloudflare's GPU network
- **TypeScript** — Type-safe request handling and API routing

## Usage

### Review Code
```bash
curl -X POST https://cf-code-reviewer.jianghenry25.workers.dev/review \
  -H "Content-Type: application/json" \
  -d '{"code": "def add(a, b): return a + b", "language": "python"}'
```

### Explain Code
```bash
curl -X POST https://cf-code-reviewer.jianghenry25.workers.dev/explain \
  -H "Content-Type: application/json" \
  -d '{"code": "const fn = (n) => n <= 1 ? n : fn(n-1) + fn(n-2)", "language": "javascript"}'
```

### Suggest Improvements
```bash
curl -X POST https://cf-code-reviewer.jianghenry25.workers.dev/suggest \
  -H "Content-Type: application/json" \
  -d '{"code": "for i in range(len(arr)): print(arr[i])", "language": "python"}'
```

## Request Format
```json
{
  "code": "your code here",
  "language": "python"
}
```

- `code` (required) — The code snippet to analyse
- `language` (optional) — Programming language for context (defaults to "unknown")

## Local Development
```bash
npm install
npm run dev
```

Note: Workers AI requires Cloudflare's network. Local dev will show the binding as unsupported — deploy to test AI features.

## Deployment
```bash
npm run deploy
```

## Author

**Henry (Htet Myat Aung)** — [GitHub](https://github.com/HtetMyatAungg) · [LinkedIn](https://linkedin.com/in/htet-myat-aung-4a370932a)

Built as part of the Cloudflare Software Engineering Internship (Summer 2026) application.
