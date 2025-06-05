# Outstanding TODO and FIXME items

The following items were discovered in the codebase and remain unresolved. They
have been documented here for future tracking.

## TODO
- `src/extension.ts:82` – use better SVG icon with light and dark variants.
- `src/extension.ts:197` – automatically remove development content from production builds.
- `src/integrations/checkpoints/CheckpointTracker.ts:135` – allow users to customise checkpoint exclusions.
- `src/core/Cline.ts:398` – handle diff requests made outside the original workspace.
- `src/core/Cline.ts:791` – init checkpoints for old tasks may rely on current workspace.
- `src/core/Cline.ts:1845` – provide clearer context when a tool action is denied.
- `src/core/Cline.ts:2571` – show progress indicator and parse images/non‑text tool responses.
- `src/core/Cline.ts:2780` – retry or surface failures when executeCommand fails.
- `src/services/tree-sitter/index.ts:8` – cache parsed project state across tasks.
- `src/api/providers/requesty.ts:76` – calculate API cost using `calculateApiCostOpenAI`.

## FIXME
- `src/integrations/terminal/TerminalProcess.ts:113` – shell integration stream sometimes inserts commas.
- `src/core/Cline.ts:898` – remove legacy tool use blocks.
- `src/core/Cline.ts:1327` – allow specifying context window for OpenAI‑compatible models.
- `src/core/Cline.ts:1350` – improve conversation truncation logic for caching and multiple context windows.
- `src/core/Cline.ts:3040` – consider blocking checkpoint initialisation for old tasks in wrong workspace.
- `src/core/Cline.ts:3332` – avoid regex when parsing mentions inside tags.
- `src/core/webview/ClineProvider.ts:1699` – investigate occasional task JSON save failures.
- `src/api/providers/openrouter.ts:142` – rely less on middle‑out transform once token estimator improves.
- `src/api/providers/openrouter.ts:225` – unnecessary delay before fetching generation details.

