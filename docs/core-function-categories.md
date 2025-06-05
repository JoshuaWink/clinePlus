# Core Function Categorization

This document groups every function in `src/core` by whether it acts on language model output (*Agent Response Handling*) or whether it performs deterministic tasks.

## Agent Response Handling

These functions interpret, transform, or directly react to the model's streamed responses.

- **assistant-message/**
  - `parseAssistantMessage()` – parse streamed tool blocks from assistant text.
  - `constructNewFileContent()` – apply streamed SEARCH/REPLACE patches.

- **Cline.ts**
  - `attemptApiRequest()` – issue an API request and yield streaming output.
  - `presentAssistantMessage()` – process streamed assistant reply blocks.
  - `recursivelyMakeClineRequests()` – recursively send model requests.
  - `executeCommandTool()` – run shell commands requested by the model.

## Deterministic Logic

Functions below manage state, workspace data, or formatting without relying on probabilistic output.

- **Cline.ts**
  - `ensureTaskDirectoryExists()`
  - `getSavedApiConversationHistory()` / `saveApiConversationHistory()`
  - `addToApiConversationHistory()` / `overwriteApiConversationHistory()`
  - `getSavedClineMessages()` / `addToClineMessages()` / `overwriteClineMessages()` / `saveClineMessages()`
  - `restoreCheckpoint()` / `saveCheckpoint()`
  - `presentMultifileDiff()` / `doesLatestTaskCompletionHaveNewChanges()`
  - `startTask()` / `resumeTaskFromHistory()` / `initiateTaskLoop()` / `abortTask()`
  - `say()` / `handleWebviewAskResponse()` / `ask()` / `sayAndCreateMissingParamError()` / `removeLastPartialMessageIfExistsWithType()`
  - `loadContext()` / `getEnvironmentDetails()`

- **assistant-message/diff.ts**
  - `lineTrimmedFallbackMatch()` – helper for fuzzy diff matching.
  - `blockAnchorFallbackMatch()` – alternate diff anchor strategy.

- **ignore/ClineIgnoreController.ts**
  - `initialize()` / `dispose()`
  - `setupFileWatcher()` / `loadClineIgnore()`
  - `validateAccess()` / `validateCommand()` / `filterPaths()`

- **mentions/index.ts**
  - `openMention()` / `parseMentions()`
  - `getFileOrFolderContent()` / `getWorkspaceProblems()`

- **prompts/responses.ts**
  - `formatResponse.*` helpers (toolDenied, toolError, clineIgnoreError, etc.)
  - `formatImagesIntoBlocks()`

- **prompts/system.ts**
  - `SYSTEM_PROMPT()`
  - `addUserInstructions()`

- **sliding-window/index.ts**
  - `getNextTruncationRange()` / `getTruncatedMessages()`

- **webview/getNonce.ts** – `getNonce()`
- **webview/getUri.ts** – `getUri()`
- **webview/ClineProvider.ts** – many async methods for state management and messaging (dispose, handleSignOut, setAuthToken, resolveWebviewView, initClineWithTask, etc.)

---

This expanded list should make it easier to locate every function in `src/core` and understand whether it depends on language model output or simply performs deterministic work.
