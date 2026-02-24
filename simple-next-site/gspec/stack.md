---
gspec-version: 1.2.1
---

# Technology Stack Definition

## 1. Overview

- **Architecture style**: Server-rendered monolith (Next.js App Router with SSR/SSG)
- **Deployment target**: Cloud — Vercel (edge/serverless rendering with built-in CDN)
- **Scale & performance**: Core content loads within 2s on typical mobile networks; lean bundles via dynamic imports and tree-shaking; responsive across desktop and mobile viewports

## 2. Open Questions & Clarifications

None — all critical technology decisions are resolved.

## 3. Core Technology Stack

### Programming Languages

- **Primary**: TypeScript 5.x (strict mode enabled)
  - *Rationale*: Type safety, predictable refactors, first-class Next.js support
- **Secondary**: N/A
- **Tooling**: ESLint (TypeScript rules), Prettier (formatting)

### Runtime Environment

- **Runtime**: Node.js 20+ LTS
  - *Rationale*: Required for Next.js; LTS ensures stability and long-term security patches
- **Container runtime**: Not required — Vercel manages the runtime environment

## 4. Frontend Stack

### Framework

- **Framework**: Next.js (latest LTS release, App Router)
  - *Rationale*: Server-rendered defaults with hydration as needed; App Router provides layouts, server components, and streaming out of the box; first-class Vercel deployment support
- **Update strategy**: Track Next.js LTS releases; upgrade within 30 days of new LTS availability

### Build Tools

- **Bundler**: Next.js built-in (SWC-based compiler + Turbopack for development)
  - *Rationale*: Zero-config, optimized for the Next.js ecosystem; SWC provides fast TypeScript transpilation
- **Build optimization**: Dynamic imports for code-splitting, tree-shaking via ES module imports, Next.js image optimization pipeline

### State Management

- **Approach**: Server-first — lean on server components and server-rendered data; client-side state kept minimal
- **Libraries**: React built-in hooks (`useState`, `useReducer`, `useContext`) for local/client state
  - *Rationale*: No global state library needed for a content-driven frontend; avoids unnecessary bundle weight
- **Data fetching**: Next.js `fetch` with caching directives in server components; SWR or server actions for any client-side data needs

### Styling Technology

- **Framework**: Tailwind CSS 4.x with design tokens for spacing, typography, colors, and elevation
  - *Rationale*: Utility-first approach aligns with component-based architecture; shared configuration keeps styles cohesive; excellent tree-shaking for production
- **CSS-in-JS**: Not used — Tailwind utilities only; no raw CSS outside Tailwind conventions
- **Responsive design**: Tailwind responsive prefixes (`sm:`, `md:`, `lg:`, `xl:`) for mobile-first breakpoints
### Iconography

- **Library**: HeroIcons (SVG-based)
  - *Rationale*: Scalable, tree-shakeable inline SVG imports; consistent theming with Tailwind; maintained by the Tailwind team

## 5. Backend Stack

**Not Applicable** — this is a frontend-only / static site project deployed to Vercel. No database, API layer, or server-side auth is required.

### Database

N/A

### Caching Layer

N/A — Vercel edge caching and Next.js built-in caching handle content delivery.

### Message Queue / Event Bus

N/A

## 6. Infrastructure & DevOps

### Cloud Provider

- **Provider**: Vercel
  - *Key services*: Edge network, serverless functions (if needed), image optimization, analytics
  - *Rationale*: Purpose-built for Next.js; predictable builds, automatic edge caching, zero-config HTTPS

### Container Orchestration

N/A — Vercel manages scaling and deployment infrastructure automatically.

### CI/CD Pipeline

- **Platform**: GitLab CI
- **Pipeline stages**:
  1. `lint` — ESLint + Prettier checks
  2. `typecheck` — `tsc --noEmit` for type safety
  3. `test` — Vitest unit/integration tests + Cypress E2E (headless)
  4. `build` — Next.js production build
  5. `deploy` — Vercel deployment (triggered on merge to main)
- **Deployment automation**: Vercel Git integration for preview deployments on merge requests; production deploy on main branch merge after pipeline passes

### Infrastructure as Code

N/A — Vercel manages infrastructure. Project configuration lives in `next.config.ts` and `vercel.json` (if needed).

## 7. Data & Storage

### File Storage

- **Static assets**: Served via Vercel's built-in CDN from the `public/` directory
- **Images**: Next.js `<Image />` component with automatic optimization (WebP/AVIF, responsive sizing)
- **Asset management**: Styled placeholders used during development; final assets swapped in before release

### Data Warehouse / Analytics

N/A

## 8. Authentication & Security

N/A — no authentication or authorization layer for this frontend-only project.

### Security Tools

- **Secrets management**: Environment variables via Vercel project settings (build-time and runtime)
- **Security scanning**: `pnpm audit` for dependency vulnerabilities; Dependabot or Renovate for automated dependency updates
- **Compliance**: HTTPS enforced by Vercel; no user data collection requiring GDPR/CCPA compliance at this stage

## 9. Monitoring & Observability

Minimal for initial launch — to be revisited as the project scales.

### Application Monitoring

Deferred — Vercel provides basic deployment and function metrics out of the box.

### Logging

Deferred — Vercel function logs available via dashboard for debugging.

### Tracing

N/A

### Error Tracking

Deferred — can add Sentry when needed. Next.js has built-in error boundaries for graceful UI failure handling.

## 10. Testing Infrastructure

### Testing Frameworks

- **Unit / Integration**: Vitest
  - *Rationale*: Fast, ESM-native, excellent TypeScript support; compatible with React Testing Library
- **Component testing**: React Testing Library
  - *Rationale*: Tests components as users interact with them; encourages accessible markup
- **E2E**: Cypress (headless in CI)
  - *Rationale*: Mature ecosystem, reliable deterministic tests with `cy.intercept()` for stubbing

### Test Data Management

- **Fixtures**: JSON fixtures in `tests/fixtures/` for consistent test data
- **Mocks**: Vitest built-in mocking for modules; `cy.intercept()` for network stubbing in E2E
- **Test isolation**: Each test suite manages its own state; no shared mutable state between tests

### Performance Testing

Deferred — Core Web Vitals monitored via Lighthouse CI or Vercel Analytics when enabled.

## 11. Third-Party Integrations

### External Services

- **Resend** — Transactional email delivery for the contact form submission endpoint.
  - *Rationale*: Simple REST API, first-class Vercel/serverless support, generous free tier (100 emails/day), no SMTP configuration needed.

### API Clients

- **Resend SDK** (`resend` npm package) — Used in the contact form Server Action to send email notifications when visitors submit the contact form.

## 12. Development Tools

### Package Management

- **Package manager**: pnpm (latest stable)
  - *Rationale*: Fast installs, strict dependency resolution prevents phantom dependencies, disk-efficient via content-addressable storage
- **Dependency management**: `pnpm-lock.yaml` committed to version control; `pnpm audit` run in CI
- **Private registry**: N/A

### Code Quality Tools

- **Linter**: ESLint with `eslint-config-next` and TypeScript rules
- **Formatter**: Prettier (configured to align with ESLint)
- **Pre-commit hooks**: Husky + lint-staged for running ESLint and Prettier on staged files
- **Type checking**: `tsc --noEmit` in CI pipeline

### Local Development

- **Project starter**: `create-next-app` (official Next.js scaffolding tool via `pnpm create next-app`)
  - *Rationale*: Provides a well-structured starting point with recommended defaults, TypeScript config, and App Router setup
- **Setup**: `pnpm install` → `pnpm dev` (Next.js dev server with Turbopack)
- **Hot reload**: Built-in via Next.js Fast Refresh
- **Environment**: `.env.local` for local environment variables (gitignored)

## 13. Migration & Compatibility

### Legacy System Integration

N/A — greenfield project.

### Upgrade Path

- **Next.js**: Track LTS releases; review changelogs and run codemods when upgrading major versions
- **Tailwind CSS**: Follow major version migration guides; design tokens minimize breaking changes
- **Dependencies**: Automated update PRs via Renovate or Dependabot; reviewed weekly

## 14. Technology Decisions & Tradeoffs

### Key Architectural Decisions

| Decision | Choice | Alternatives Considered | Rationale |
|---|---|---|---|
| Framework | Next.js (App Router) | Remix, Astro, Nuxt | Best Vercel integration; mature SSR/SSG; React ecosystem |
| Styling | Tailwind CSS | CSS Modules, Styled Components | Utility-first aligns with component architecture; zero runtime cost; design token support |
| Testing | Vitest + Cypress | Jest + Playwright | Vitest is faster and ESM-native; Cypress is mature for E2E with reliable stubbing |
| Package manager | pnpm | npm, yarn | Strict resolution prevents phantom deps; faster installs; disk-efficient |
| Deployment | Vercel | Netlify, AWS Amplify, Cloudflare Pages | Purpose-built for Next.js; edge caching; zero-config previews |
| CI/CD | GitLab CI | GitHub Actions | Aligns with existing team infrastructure and workflow |

### Risk Mitigation

| Risk | Mitigation | Fallback |
|---|---|---|
| Next.js breaking changes on major upgrade | Pin to LTS; test upgrades in preview branch | Delay upgrade; apply security patches only |
| Vercel vendor lock-in | Keep Next.js config portable; avoid Vercel-only APIs where possible | Self-host via `next start` on any Node.js platform |
| Tailwind major version migration | Use design tokens abstraction layer; follow official migration guides | Gradual migration with compatibility layer |
