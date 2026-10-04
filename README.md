# WhatsApp Sales Agent

**Configurable WhatsApp sales assistant for small shops. The owner sets products, tone, pricing limits and handoff rules in a dashboard, with no redeploys.**

> **This is a proprietary project. Source code is private. This page showcases the system's architecture and results.**

**Case study page:** [https://jryahia.github.io/showcase-whatsapp-sales-agent/](https://jryahia.github.io/showcase-whatsapp-sales-agent/)

![WhatsApp Sales Agent](assets/01-dashboard-products.png)

## Problem it solves

Small businesses get product and price questions on WhatsApp all day. Hardcoded bots break whenever the catalog or policy changes, and unconstrained ones promise discounts the shop cannot honor. This agent builds its behavior from what the owner configures, and enforces pricing limits on the server.

## Architecture

![Architecture](assets/architecture.svg)

1. An inbound WhatsApp message arrives through a Twilio webhook.
2. Guardrails check for handoff triggers first. Complaints or explicit requests go straight to a human.
3. Otherwise the agent answers using the business profile, catalog, personality and rules stored in the database.
4. Orders are validated server-side against pricing limits, whatever was said in chat.

## Key features

- Catalog, personality, business rules and handoff rules editable from the dashboard
- Changes apply on the next message, with no redeploy
- Handoff to a human before the LLM is called when a trigger matches
- Pricing floors and discount caps enforced in the backend
- Encrypted provider credentials; DeepSeek or OpenAI

## Tech stack

![Python](https://img.shields.io/badge/Python-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![FastAPI](https://img.shields.io/badge/FastAPI-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![Twilio](https://img.shields.io/badge/Twilio-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![DeepSeek / OpenAI](https://img.shields.io/badge/DeepSeek%20/%20OpenAI-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![Jinja2](https://img.shields.io/badge/Jinja2-161b22?style=for-the-badge&labelColor=161b22&color=161b22)

## What it does in practice

- Answers product and pricing questions from live catalog data instead of a fixed script.
- Makes over-promised discounts impossible to turn into orders.

## Screenshots

**Product catalog the agent answers from**

![Product catalog the agent answers from](assets/01-dashboard-products.png)

**Pricing rules enforced on every order**

![Pricing rules enforced on every order](assets/03-dashboard-pricing.png)

---

Built by [Yahya Jarray](https://github.com/jryahia). Interested in a similar system? [Get in touch](mailto:yahiajarray43@gmail.com).
