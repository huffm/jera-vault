# Public Copy Rules

## Purpose

These rules keep Jera Technologies public copy accurate, credible, and consistent.

## Rules

- Write in a calm, senior, product minded tone.
- Keep copy concise and practical.
- Use proper casing.
- Avoid dashes in public facing copy where possible.
- Prefer concrete workflow language over broad AI claims.
- Describe products as Jera built products, owned products, product examples, or solution examples.
- Do not imply paid client work unless explicitly provided later.
- Do not invent clients, metrics, testimonials, revenue, adoption, or results.
- Keep employer related work high level and non sensitive.
- Do not expose private prompts, scoring rules, unreleased product strategy, or monetization details.

## AI Language

Use AI language only when it describes a real workflow or capability. Preferred framing:

- AI supported analysis.
- Structured AI workflows.
- Structured analysis.
- Signal gathering.
- Reviewable outputs.
- Reviewable decision artifacts.
- Human review.
- Decision support.

Avoid exposing internal method terms on public pages unless Malcolm explicitly approves them for launch.

## Product Language

Products should feel credible and business facing. They should demonstrate what Jera Technologies can build through its engineering services.

## Sports Product Language

The matchup analyzer should be described as a sports matchup analysis and decision support application. Do not center the product around gambling, picks, guaranteed predictions, or betting profits.

## Current Website Copy Check

Slice 1 public site copy was checked for restricted public terms. The current website source does not use the restricted casual product or betting centered terms.

Internal truth boundaries remain in the vault rather than being displayed as public page copy.

## Public Exposure Reduction

Slice 2 reduced public exposure of internal method language.

Avoid leading public pages with:

- DAI
- Retrieval
- Evaluation
- Synthesis
- Internal stage sequencing
- Prompt logic
- Scoring rules
- Internal cognitive architecture

Preferred public language:

- Structured analysis
- Signal gathering
- Reviewable outputs
- Clear decision artifacts
- Productized software workflows
- Structured Analysis Pipeline
- Reviewable Analysis System

The generated HTML was checked after Slice 2 and does not expose `DAI`, retrieval, evaluation, or synthesis.

## Launch Copy Check

The site now includes a repeatable public copy exposure check:

`npm run copy-check`

The check scans generated HTML in `dist` for restricted public terms including DAI, retrieval, evaluation, synthesis, private scoring rules, internal prompt logic, cognitive architecture, betting model, prediction engine, guaranteed picks, and profit.

Run it after `npm run build` before preview deployment.

## Contact Copy And Links

Use `support@jeratechnologies.com` for public contact email.

Do not use retired placeholder email addresses or placeholder domains in public source, generated HTML, or vault launch notes.

Use mailto links for v1 contact behavior. A backend contact form should only be added in a future implementation slice with explicit approval.
