# Frontend

Frontend design & animation workspace for QuantumindSSI, wired to a curated set of
UI component registries and MCP servers for AI-assisted component work across the
**Svelte** and **React** ecosystems.

## Repository layout

| Path | Purpose |
| --- | --- |
| `svelte/components.json` | shadcn-svelte registry manifest (Svelte / SvelteKit) |
| `react/components.json` | shadcn registry manifest (React / Next.js) |
| `.mcp.json` | Portable MCP server definitions (frontend design + animation) |
| `files.md` | Source list of the Bhide Svelte component sites |

## Component registries

### Svelte (`svelte/components.json`)

Built on the **Bhide Svelte** ecosystem (shadcn-svelte registries served at `/r/{name}.json`):

| Alias | Registry | Offers |
| --- | --- | --- |
| `@sv-animations` | https://sv-animations.vercel.app/r/{name}.json | 50+ animated components (motion-sv) |
| `@sv-table` | https://sv-table.vercel.app/r/{name}.json | TanStack datatables |
| `@sv-blocks` | https://sv-blocks.vercel.app/r/{name}.json | 150+ UI & marketing blocks |
| `@sv-efferd` | https://sv-efferd.pages.dev/r/{name}.json | 60+ marketing blocks |
| `@sv-matrix` | https://sv-matrix.vercel.app/r/{name}.json | 50+ loaders / spinners |
| `@sveltebits` | https://sveltebits.xyz/r/{name}.json | React Bits, Svelte port |

Install a component:

```bash
npx shadcn-svelte@latest add @sv-efferd/hero-one
```

### React (`react/components.json`)

| Alias | Registry | Offers |
| --- | --- | --- |
| `@magicui` | https://magicui.design/r/{name}.json | Animation components |
| `@aceternity` | https://ui.aceternity.com/registry/{name}.json | 200+ animated components |
| `@kokonutui` | https://kokonutui.com/r/{name}.json | Animated UI blocks |
| `@cultui` | https://cult-ui.com/r/{name}.json | Motion components |
| `@skiper` | https://skiper-ui.com/r/{name}.json | 100+ components |
| `@reactbits` | https://reactbits.dev/r/{name}.json | 165+ animated components |
| `@originui` | https://originui.com/r/{name}.json | 500+ components |

Install a component:

```bash
npx shadcn@latest add @magicui/marquee
```

## MCP servers

`.mcp.json` defines the frontend design & animation MCP servers. Merge these into your
AI agent's MCP config (opencode `opencode.jsonc`, Cursor `.cursor/mcp.json`,
Claude `.mcp.json`, etc.).

| Server | Type | Purpose |
| --- | --- | --- |
| `shadcn` | local (npx) | Universal React registry client (reads `react/components.json`) |
| `shadcn-svelte` | local (npx) | Svelte registry client (reads `svelte/components.json`) |
| `21st` | remote (http) | 21st.dev generative UI, search, logos, themes — **requires `X_21ST_API_KEY`** |
| `magicui` | local (npx) | Magic UI animation components |
| `motion` | remote (http) | Motion.dev AI Kit — CSS springs, docs, perf audits |

The `shadcn` and `shadcn-svelte` servers are **project-scoped**: run your agent from the
directory containing the relevant `components.json` (or copy it to your project root) so
the registry aliases resolve.

### Secrets

Do not commit API keys. 21st.dev requires:

```bash
export X_21ST_API_KEY="your-key-from-https://21st.dev/mcp"
```

## Notes

- `sv-particles` (Svelte QBlocks) and `sv-agentation` from `files.md` are **not**
  registries. `sv-particles` is CLI/jsrepo-only (no public `/r/` index); `sv-agentation`
  is an npm dev-tool (`pnpm add sv-agentation`) for UI annotation.
