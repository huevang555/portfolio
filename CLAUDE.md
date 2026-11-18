# CLAUDE.md — Personal Portfolio

## Project
Personal portfolio website for a full-stack developer in Laos.
Design rules live in `DESIGN.md` — read it before any UI work.
Original planning brief: `PORTFOLIO_BRIEF.md`.

- **Audience:** tech / IT companies that build apps and websites, especially teams that
  use AI to speed up development. Tone: professional, concrete, engineering-focused.
- **Positioning:** full-stack engineer who builds realtime systems that move real money,
  and who uses AI tools (e.g. Claude Code) effectively in daily development.
- **Language:** English only for v1. All strings still live in `messages/en.json`
  so a Lao locale can be added later without refactoring.
- **Domain (planned):** `vanghue.dev` — not purchased yet.

## Owner info
- GitHub: https://github.com/huevang555
- Email: huevang999@gmail.com
- Photo: `assets/profile.jpg` (move to `public/` after scaffolding; serve via `next/image`)
- Display name, LinkedIn, CV PDF: TBD — use placeholders until provided.

## Stack
- Next.js (App Router) + TypeScript (strict)
- Tailwind CSS v4 + shadcn/ui
- Motion (framer-motion) — subtle only, always respect `prefers-reduced-motion`
- MDX for case studies (`/work/[slug]`) and blog
- i18n: `next-intl` with a single `en` locale for now
- Fonts, colors, layout: see `DESIGN.md` (Noto Sans Lao if Lao is added)
- Design skill: `.claude/skills/frontend-design` (official Anthropic skill) — use for UI work
- Hosting: Vercel

## Commands
- `pnpm dev`        — start dev server
- `pnpm build`      — production build (must pass before "done")
- `pnpm lint`       — ESLint
- `pnpm typecheck`  — `next typegen && tsc --noEmit` (route types like `LayoutProps` are generated)

## Next.js version
Next.js 16 (+ React 19.3) — newer than most training data. Follow `AGENTS.md`: read the
bundled docs in `node_modules/next/dist/docs/` before using an API you are unsure of.

## Conventions
- No hard-coded user-facing text in components; read it from `messages/en.json`.
- Code, comments, commit messages: English.
- Components: small, typed props, server components by default; `"use client"` only when needed.
- Accessibility: semantic HTML, alt text, visible keyboard focus, AA contrast.
- Support light + dark mode.

## Definition of done
1. `pnpm build`, `pnpm lint`, `pnpm typecheck` pass.
2. Page checked in a real browser at 375px and desktop width (screenshots), no console errors,
   no horizontal scroll.

## Confidentiality (hard rules)
Work content comes from the user's employer. On the site and in this repo:
- NO source code, server/DB names, schema/field names, internal URLs, real money amounts,
  customer data, or security weaknesses from the company.
- Describe work at a high level only: problem → approach → result. Blur any screenshots.
- Do NOT name the employer until the user confirms permission.
- Never read or copy files from the employer's workspace folder (outside this repo).
- `PORTFOLIO_BRIEF.md` is git-ignored (local only) — never commit it or quote it on the site.
- Case study text: the user approves every word before publishing.

## Working with the user
- Reply in **Lao**; keep technical terms (component, deploy, branch, API…) in English.
- Short answers: answer first, then only needed details; prefer bullets/tables.
- Propose → wait for approval → build. No big changes without agreement.
- Use they/them for the user.
