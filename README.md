# @lxgicstudios/openapi-mock

[![npm version](https://img.shields.io/npm/v/@lxgicstudios/openapi-mock)](https://www.npmjs.com/package/@lxgicstudios/openapi-mock)
[![license](https://img.shields.io/npm/l/@lxgicstudios/openapi-mock)](LICENSE)
[![node](https://img.shields.io/node/v/@lxgicstudios/openapi-mock)](package.json)

Spin up a mock HTTP server from any OpenAPI 3.x JSON spec. Auto-generates realistic responses, validates requests, simulates latency. Zero dependencies.

## Install

```bash
npm install -g @lxgicstudios/openapi-mock
```

Or run directly:

```bash
npx @lxgicstudios/openapi-mock ./petstore.json
```

## Usage

```bash
# Start mock server on default port
openapi-mock ./petstore.json

# Custom port with 200ms latency
openapi-mock ./api-spec.json --port 8080 --delay 200

# With request validation
openapi-mock ./spec.json --validate

# JSON request logs
openapi-mock ./spec.json --json
```

## Features

- Reads OpenAPI 3.x JSON specs and auto-generates endpoints
- Realistic mock data from schema types (string, number, boolean, array, object)
- Handles `$ref` references within components/schemas
- Respects `enum` values and `format` hints (email, uri, uuid, date-time, ipv4)
- Supports `allOf`, `oneOf`, `anyOf` composition
- Request body validation against schemas (with `--validate`)
- Latency simulation for realistic testing
- Proper HTTP status codes from spec
- Colorful request logging
- Zero external dependencies (built-in `http` module)

## Options

| Flag | Description |
|------|-------------|
| `--port <n>` | Port to listen on (default: 3000) |
| `--delay <ms>` | Add latency to responses in milliseconds |
| `--validate` | Validate incoming request bodies against schemas |
| `--json` | Output request logs as JSON |
| `--help` | Show help message |

## How It Works

1. Reads your OpenAPI 3.x JSON spec file
2. Registers all paths and methods as routes
3. When a request comes in, it matches the route and method
4. Generates mock response data based on the response schema
5. Returns the mock data with proper status codes

The mock data generator handles:
- **Strings**: format-aware (email, uuid, uri, date-time, ipv4, hostname)
- **Numbers/Integers**: respects min/max bounds
- **Booleans**: alternating true/false
- **Arrays**: generates 2 items per array
- **Objects**: populates all defined properties
- **Enums**: cycles through defined values
- **Refs**: resolves `$ref` pointers to components/schemas

## License

MIT

---

**Built by [LXGIC Studios](https://lxgicstudios.com)**

🔗 [GitHub](https://github.com/lxgicstudios) · [Twitter](https://x.com/lxgicstudios)

💡 Want more free tools like this? We have 100+ on our GitHub: [github.com/lxgicstudios](https://github.com/lxgicstudios)
