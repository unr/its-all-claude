# its-all-claude Constitution

<!--
Sync Impact Report:
===================
Version Change: N/A → 1.0.0
Rationale: Initial constitution for personal blog project

Modified Principles: N/A (initial creation)
Added Sections:
  - Core Principles (5 principles covering Component-First, Content-First, Design System, Type Safety, Performance)
  - Technology Standards
  - Development Workflow
  - Governance

Removed Sections: N/A

Templates Requiring Updates:
  ✅ .specify/templates/plan-template.md (constitution check section aligned)
  ✅ .specify/templates/spec-template.md (requirements aligned with principles)
  ✅ .specify/templates/tasks-template.md (task categorization aligned)

Follow-up TODOs:
  - Ratification date set to 2025-10-18 (today) as initial constitution
-->

## Core Principles

### I. Component-First Architecture

All UI features MUST be built using existing Nuxt UI components unless custom implementation is explicitly required and justified. Custom components MUST follow Vue 3 Composition API with `<script setup>` syntax, utilize Nuxt auto-imports, and maintain consistency with the Nuxt UI design system.

**Rationale**: Leveraging Nuxt UI reduces development time, ensures accessibility compliance, and maintains visual consistency. Custom components introduce maintenance burden and must demonstrate clear value over existing solutions.

### II. Content-First Design

The blog exists to serve three content types: personal stories, technical developer posts, and video game reviews. All features, layouts, and interactions MUST prioritize content readability and discoverability. Navigation, typography, and layout decisions MUST enhance the reading experience.

**Rationale**: A personal blog's success depends on content consumption. Features that distract from or compete with content violate the project's core purpose.

### III. Design System Consistency

The project uses orange as the core theme color. All color choices, spacing, typography, and UI patterns MUST align with this branding and follow Tailwind CSS conventions. Visual decisions MUST be documented and reusable through Tailwind config or design tokens.

**Rationale**: Consistent branding builds recognition and professionalism. Ad-hoc styling creates maintenance burden and dilutes brand identity.

### IV. Type Safety (NON-NEGOTIABLE)

All TypeScript code MUST compile without errors. Use of `any` type is prohibited except when interfacing with untyped third-party libraries, and MUST be documented with a justification comment. Vue components MUST use proper TypeScript typing for props, emits, and composables.

**Rationale**: Type safety catches bugs at compile time, improves IDE support, and serves as living documentation. The cost of strict typing is negligible compared to runtime debugging.

### V. Performance & Static Generation

The blog MUST be statically generated for optimal performance. Pages MUST load in under 2 seconds on 3G connections. Images MUST use Nuxt Image with proper optimization. Lighthouse scores MUST maintain: Performance >90, Accessibility >95, Best Practices >90, SEO >95.

**Rationale**: Personal blogs compete with millions of alternatives. Poor performance directly impacts reader retention and search engine rankings. Static generation provides the best performance-to-complexity ratio.

## Technology Standards

**Framework**: Nuxt 4 with Vue 3 and TypeScript
**Content Management**: Nuxt Content for markdown-based posts
**Component Library**: Nuxt UI (primary), custom components only when justified
**Styling**: Tailwind CSS with orange theme customization
**Image Optimization**: Nuxt Image module
**Testing**: Nuxt Test Utils (when tests are required)
**Linting**: ESLint with @nuxt/eslint configuration
**Deployment Target**: Static site generation (SSG) via `nuxt generate`

**Prohibited**:
- Runtime server dependencies (must be statically generatable)
- Inline styles bypassing Tailwind
- Component libraries other than Nuxt UI without explicit approval
- TypeScript `any` without documented justification

## Development Workflow

### Code Style Requirements
- Use `<script setup>` syntax for all Vue components
- Rely on Nuxt auto-imports (no explicit imports for Nuxt APIs, components, composables)
- Follow PascalCase for components, camelCase for composables/utils
- Maintain consistent indentation and formatting per ESLint rules
- NO code comments unless documenting complex business logic or TypeScript edge cases

### Quality Gates
Before any feature is considered complete:
1. TypeScript MUST compile without errors (`nuxt build`)
2. ESLint MUST pass without warnings (`nuxt lint` or equivalent)
3. Lighthouse audit MUST meet minimum scores (Performance >90, Accessibility >95)
4. All Nuxt Content markdown MUST render correctly
5. Static generation MUST succeed (`nuxt generate`)

### Feature Development Process
1. **Specification**: Define user stories and acceptance criteria
2. **Design Review**: Verify alignment with orange branding and Nuxt UI patterns
3. **Implementation**: Build using existing components first, justify custom work
4. **Validation**: Run quality gates, test on mobile viewports
5. **Documentation**: Update relevant docs only if feature changes workflows

## Governance

This constitution supersedes all other development practices and preferences. All code reviews, feature designs, and architectural decisions MUST verify compliance with these principles.

**Amendment Process**:
- Amendments require documented rationale and impact analysis
- Version bumping follows semantic versioning:
  - **MAJOR**: Principle removal or backward-incompatible governance changes
  - **MINOR**: New principles added or existing principles materially expanded
  - **PATCH**: Clarifications, wording improvements, non-semantic refinements
- Amendments MUST update version, last amended date, and sync impact report
- Consistency check MUST be performed across all `.specify/templates/` files

**Complexity Justification**:
Any violation of constitution principles (e.g., custom component when Nuxt UI component exists, use of `any` type, third-party component library) MUST be documented in the relevant specification or plan with:
- The specific constraint being violated
- Why the violation is necessary
- What simpler alternative was rejected and why

**Compliance Reviews**:
- All specifications MUST include a "Constitution Check" section
- Pull requests (when used) MUST reference applicable principles
- Feature plans MUST document principle alignment before implementation begins

**Version**: 1.0.0 | **Ratified**: 2025-10-18 | **Last Amended**: 2025-10-18
