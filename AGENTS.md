# Agent Guidelines for its-all-claude

## Commands

- **Dev**: `pnpm dev` (starts Nuxt dev server on <http://localhost:3000>)
 **Build**: `pnpm build` (production build with Nuxt)
- **Preview**: `pnpm preview` (preview production build)
- **Install**: `pnpm install` (install dependencies)
- **Lint**: ESLint is configured via `@nuxt/eslint` (check `.nuxt/eslint.config.mjs` for rules)
- **Tests**: Test utils available via `@nuxt/test-utils` module

## Code Style

- **Framework**: Nuxt 4 + Vue 3 with TypeScript
- **Imports**: Use Nuxt auto-imports (components, composables, utils) - no explicit imports needed for Nuxt APIs
- **Components**: Use `<script setup>` syntax for Vue 3 composition API
- **Formatting**: Follow ESLint config from `@nuxt/eslint` (extends Nuxt defaults)
- **Types**: TypeScript enabled via Nuxt project references (`.nuxt/tsconfig.*.json`)
- **Naming**: PascalCase for components, camelCase for composables/utils
- **Modules**: Using @nuxt/content, @nuxt/ui, @nuxt/image, @nuxt/scripts
- **Error Handling**: Use Nuxt error handling patterns (e.g., `createError`, `showError`)

## Project Structure

- `app/` - Application source (app.vue is root component)
- `public/` - Static assets
- Auto-import enabled for components, composables, and Nuxt utilities

## Rules

- Before you do any work, MUST view files in .prompt/sessions/context_session_x.md file to get the full context (x being a slug related to the session we are operating in, if the file doesn't exist create one, if it already exists read it and verify the contents are related to the current session, if they are not related create a new session file instead)
- context_session_x.md should contain most of the context of what we did, overall plan, and sub agents will continuously add context to the file
- After you finish the work, MUST update the .prompt/sessions/context_session_x.md file to make sure others get full context of what you did
- When you're finished with a task that wrote new code, ask if we'd like to have technical-doc-writer look for changes and update the documentation if needed

### Sub Agents

You have access to these sub agents:

- nuxt-vue-expert: all tasks related to code, nuxt, vue, frontend, js, ts work HAVE TO consult this agent
- blog-design-specialist: all tasks related to creating designs HAVE TO consult this agent
- blog-content-editor: all tasks related to creating, reviewing, editing, proposing blog content HAVE TO consult this agent

Sub agents will do research about the implementation, but you will do the actual implementation; When passing a task to sub agent, make sure you pass the context file, e.g. `.prompt/sessions/context_session_x.md`
After each sub-agent finishes its work, review their output (e.g., documentation, plans) to get the full context before you start executing. The `technical-doc-writer`, for instance, will provide a summary of the documentation it has written.
