# Open DeepSeek Harness

A custom fork of the [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) containing skills and tools for **contract-based development**.

English | [中文](README.zh.md)

## About this fork

This fork builds on DeepSeek Harness's plugin architecture (everything is a plugin, powered by [Cordis](https://github.com/cordiverse/cordis)) and turns the harness toward **contract-based development**: authoring software against explicit, machine-checkable contracts and letting those contracts drive, verify, and gate the work of the agent.

Contract-based development here means:

- **Contracts come first.** Before implementation begins, the surface is defined explicitly — type graphs, API and service schemas, tool signatures, and the invariants those surfaces must satisfy — rather than inferred from natural-language instructions.
- **Skills author and maintain contracts.** The bundled skills capture workflows for drafting, refining, and reviewing contract definitions, and keep contract sources in sync as code evolves.
- **Tools verify contracts in the loop.** Contract-aware tools inspect generated and written code against the declared surfaces, wire contract checks into the agent loop, and surface violations as actionable failures instead of silent drift.
- **Gates enforce conformance.** The repo's gate infrastructure is reused so contract conformance is a mechanical check on every change, not a manual review step.

The fork keeps upstream DeepSeek Harness functionality — LLM capabilities, shell, filesystem, subprocess, terminal, web, LSP, skill, workflow, compaction, and per-session agent composition from `cordis.yml` — and layers the contract-first skills and tools on top of that foundation.

DeepSeek Harness is in _developer preview_ and iterating rapidly. **THERE WILL BE COMPATIBILITY-BREAKING CHANGES.**

Review the [safety notice](SAFETY.md) before running the project.

Documentation: [https://deepseek-harness.github.io/deepseek-harness/](https://deepseek-harness.github.io/deepseek-harness/)

## Run

Install `Node.js`, then run:

```sh
npx @deepseek-ai/dsh web
```

The command starts the Web UI at `http://127.0.0.1:3080` by default and opens it in the default browser for a local launch. Pass `--no-open` to run the server without opening a browser.

To run from source:

```sh
git clone git@github.com:BOLD-ENGINEERING/open.deepseek.harness.git
cd open.deepseek.harness
pnpm install
pnpm run build
pnpm dsh web
```

`pnpm run build` prepares the repository artifacts. `pnpm dsh web` uses those built artifacts without rebuilding.

## Development

Start with the [development guide](docs/development.md) and [architecture documentation](docs/architecture.md). The upstream [project overview](docs/index.md) and per-folder documentation live under `docs/`.

For agents, follow [AGENTS.md](AGENTS.md).

## License

[MIT](LICENSE)

Third-party dependencies and their licenses are disclosed in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
