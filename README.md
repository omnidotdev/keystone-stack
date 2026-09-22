# 🗝️ Keystone

Keystone is an AI web builder: describe a site, Keystone generates it, you refine
it turn by turn, then publish it. This metarepo orchestrates the Keystone services
for local development with [Tilt](https://tilt.dev). Apache-2.0.

Services:

- [`keystone-app`](services/keystone-app) - the builder UI (chat-first editor,
  live preview, publish flow) plus the marketing landing and pricing pages. Built
  with [TanStack Start](https://tanstack.com/start).
- [`keystone-api`](services/keystone-api) - the API and generation engine
  (Elysia + Postgraphile v5 + Drizzle, Anthropic SDK). See its README for the
  engine, publish pipeline, and ecosystem blocks.

## Prerequisites

- [Tilt](https://tilt.dev)

## Local Development

### Getting Started

1. Copy the template configuration:

```sh
cp services.yaml.template services.yaml
```

2. Configure the services as needed. To disable a service, comment it out. Any
   included services will be locally cloned.

3. Each service has its own setup (env vars, a local Postgres for `keystone-api`).
   Consult each service's README before first run.

4. Start the development environment:

```sh
tilt up
```

The `Tiltfile` automatically pulls in resources from any nested `Tiltfile`s it
discovers.

### Configuration

Each service in `services.yaml` can specify:

| Key | Description |
|-----|-------------|
| `repo` | Git repository URL for cloning |
| `path` | Local path override (defaults to `services/service-name`) |
| `env` | Environment variables to set for the service |

> 💡 If nested repos are cloned within this metarepo and you open it in your IDE,
> directories may be marked as ignored due to `.gitignore` patterns. To work
> around this, open services in their own directory (e.g., a separate VS Code
> workspace unit).

## License

The code in this repository is licensed under Apache 2.0, &copy;
[Omni LLC](https://omni.dev). See [LICENSE.md](LICENSE.md) for more information.
