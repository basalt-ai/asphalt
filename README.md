<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo_white.png" />
  <source media="(prefers-color-scheme: light)" srcset="assets/logo.png" />
  <img src="assets/logo.png" alt="Asphalt" width="200" />
</picture>

<br>

**Self-improving engine for production AI agents** — Autonomous optimization that connects business metrics to agent improvements.

**[Join Discord](https://discord.gg/yW2RyZKY)** · **[Share Your Pain Points](https://github.com/basalt-ai/asphalt/discussions/1)**

<br>

![Build Status](https://github.com/basalt-ai/asphalt/actions/workflows/test.yml/badge.svg)
[![npm version](https://img.shields.io/npm/v/@basalt-ai/asphalt.svg)](https://www.npmjs.com/package/@basalt-ai/asphalt)
[![License: Apache-2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Discord](https://img.shields.io/discord/1471362791884455980?color=7289da&label=Discord&logo=discord&logoColor=white)](https://discord.gg/yW2RyZKY)

<br />

### Part of the Basalt Stack

<p>
  <strong>Cobalt</strong> (Testing) + <strong>Diamond</strong> (Datasets) + <strong>Limestone</strong> (Judges) + <strong>Asphalt</strong> (Optimization)
</p>

</div>

---

## The Problem: AI Agents Are Static Once Deployed

**Manual observation and prompt tweaking cycles.** Your agent goes live, performance degrades, and you're stuck manually monitoring logs, running evals, and tweaking prompts. The feedback loop takes weeks, and every improvement requires human intervention.

**Disconnect from business metrics.** You optimize for eval scores that don't correlate with business value. Your agent gets 90% on accuracy tests while customer satisfaction plummets and conversion rates drop.

**No way to safely test improvements on live traffic.** You want to try a new prompt or reasoning approach, but testing on real users is terrifying. One bad deployment can damage customer relationships and business metrics.

**Slow feedback loops from deployment to optimization.** It takes weeks to identify performance issues, weeks more to develop fixes, and weeks to validate improvements. Your agent stays broken while competitors move faster.

**Agents become stale over time.** User behavior changes, product features evolve, and edge cases emerge. Your static agent can't adapt, so performance gradually degrades until you're forced into expensive manual overhauls.

## Why This Kills Production AI

**Competitive disadvantage through slow iteration.** While you're stuck in manual optimization cycles, competitors with better tooling ship improvements weekly. Your static agents fall behind market demands.

**Wasted optimization effort on vanity metrics.** You spend weeks improving eval scores that don't drive business value, while real performance issues go unaddressed. Resources burned, problems unsolved.

**Fear of deployment leads to over-conservative agents.** Because you can't safely test improvements, you deploy overly cautious systems that underperform. Innovation dies in the name of risk management.

**Expensive firefighting when problems emerge.** Production issues require emergency manual intervention, pulling engineering teams off other priorities. Every outage is a crisis instead of an automatic correction.

**Knowledge doesn't transfer between agents.** Each agent optimization starts from scratch. Learnings from your customer support bot don't help your sales assistant, so you repeat the same expensive discovery process.

## What Should Exist Instead

**Autonomous optimization loops** that continuously monitor business metrics, generate safe agent improvements, test them on controlled traffic, and promote only statistically significant wins.

**Business signal integration** that directly connects agent performance to revenue, customer satisfaction, operational efficiency, and other metrics that actually matter to your business.

**Safe mutation engines** that generate semantically similar but potentially better-performing agent variants, with automatic rollback if performance degrades.

**Controlled experimentation** with proper A/B testing, statistical significance thresholds, and progressive rollouts that protect user experience while enabling rapid iteration.

**Compounding knowledge systems** that accumulate learnings over time and transfer successful optimizations across different agents and use cases.

## Join the Movement

We're building Asphalt to enable truly autonomous agent optimization in production. But we need to understand your specific deployment challenges first.

**[Tell us about your production AI struggles →](https://github.com/basalt-ai/asphalt/discussions/1)**

What challenges do you face?
- Manual observation and prompt tweaking cycles?
- Disconnect between agent performance and business metrics?
- No way to safely test improvements on live traffic?
- Agents that become stale once deployed?
- Slow feedback loops from deployment to optimization?

Your experiences directly shape what we build. Every production pain point shared helps us create better optimization tools for the entire AI development community.

⭐ **Star this repo to follow our progress** — we'll be sharing our approach to autonomous agent optimization as we validate the core problems.

---

**Built and maintained by [Basalt](https://getbasalt.ai). Open source forever under Apache 2.0.**