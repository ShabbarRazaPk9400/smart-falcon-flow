# smart-falcon-flow

![CI](https://img.shields.io/github/actions/workflow/status/ShabbarRazaPk9400/smart-falcon-flow/ci.yml?branch=main&label=CI) ![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-3178C6) ![License](https://img.shields.io/github/license/ShabbarRazaPk9400/smart-falcon-flow?color=blue) ![Version](https://img.shields.io/badge/version-2.6.2-green)

smart-falcon-flow is a TypeScript SDK for REST API integration -- a typed Client class with get/post/put/delete methods, configurable base URL, max retries with exponential backoff, and full TypeScript type definitions for responses. Zero runtime dependencies (uses native fetch). Tested with Vitest and mocked responses.

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Running Tests](#running-tests)
- [Contributing](#contributing)
- [Changelog](#changelog)
- [License](#license)

## Features

- Client class with get/post/put/delete method wrappers
- Configurable base URL and API key
- Built with tsup for CJS + ESM dual output with .d.ts files
- Tree-shakeable and side-effect free for bundlers
- Vitest test suite with mocked responses
- Works in both Node.js and browser environments

## Prerequisites

- Node.js 16 or higher
- TypeScript 5.0 or higher
- npm, yarn, or pnpm

## Installation

```bash
npm install smart-falcon-flow
# or
yarn add smart-falcon-flow
# or
pnpm add smart-falcon-flow
```

## Usage

```typescript
import { Client } from 'smart-falcon-flow';
import type { ApiResponse } from 'smart-falcon-flow';

const client = new Client({
  apiKey: process.env.API_KEY!,
  baseUrl: 'https://api.example.com',
  maxRetries: 3,
});

// GET request with typed response
const data = await client.get<ApiResponse<{ id: string; name: string }>>('/items/1');
console.log(data.data.name);

// POST request
const created = await client.post('/items', { name: 'New Item', value: 42 });

// Automatic retry with exponential backoff on failure
// The client retries up to maxRetries times with 2^attempt * 1000ms delay
```

## Project Structure

```
smart-falcon-flow/
├── src/
│   ├── client.ts
│   └── index.ts
├── tests/client.test.ts
├── package.json  tsconfig.json  tsup.config.ts
├── README.md  LICENSE  CHANGELOG.md  CONTRIBUTING.md  CODE_OF_CONDUCT.md
├── .github/
│   ├── workflows/ci.yml
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
└── .gitignore
```

## Running Tests

```bash
npm test
# watch mode
npm test -- --watch
```

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

Quick start:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make your changes and run tests (see [Running Tests](#running-tests) above)
4. Commit with a clear message: `git commit -am 'Add: my feature'`
5. Push to your fork: `git push origin feature/my-feature`
6. Open a Pull Request

Please ensure all tests pass before submitting a pull request.

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for a list of changes and version history.

## License

This project is licensed under the MIT -- see the [LICENSE](LICENSE) file for details.

Copyright (c) 2026 chen tanaka.

## Acknowledgements

- Built with TypeScript, tsup, and Vitest
- CI/CD powered by [GitHub Actions](https://github.com/features/actions)
- Badges by [shields.io](https://shields.io)
- Inspired by best practices from the open-source community
