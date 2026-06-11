# Frequently Asked Questions

**Page:** https://www.thebermuda.us/#faqs

## General

**What is Bermuda Rater?**
A rating engine and integration platform for carriers, MGAs, and agencies enabling real-time quote generation, API connections, and automated workflows powering customer portals and AMS systems. Learn more: https://www.thebermuda.us/#product

**Who is it for?**
Bermuda focuses on enterprise insurance agencies — operations with custom workflows, multiple data sources, and high policy volume. Also serves carriers, MGAs, and digital agencies building insurance technology. Integrates with rating APIs, CRMs, conversion tools, and document systems.

## AI Agents & Real-Time Data

**Can my own AI agent use Bermuda?**
Yes — Bermuda is agent-agnostic. The platform is exposed as MCP (Model Context Protocol) tool servers, so Claude, ChatGPT, or your custom agent connects natively to quoting, policy data, payments, and carrier uploads — live data in, actions out. Access is OAuth-authenticated and default-deny: each agent uses only the tools you explicitly permit, with input-level guardrails like payment caps. Details: https://www.thebermuda.us/docs/md/agentic-ai.md

**How do you control what an AI agent is allowed to do?**
Every agent authenticates via OAuth and is governed by a default-deny policy engine: it can only call the tools you explicitly permit. Policies go down to input level — for example, capping the payment amount an agent can process — and every tool call is logged and monitored.

**How is Carrier Downloads different from IVANS?**
IVANS is batch — downloads are hours old by the time they reach your AMS. Carrier Downloads reads due amounts, due dates, late fees, and statuses live from carrier portals at the moment of action, which is what makes payment and cancellation automation safe to run. More: https://www.carrierdownloads.com

**How much does it cost?**
Pricing is custom and scoped to your agency's workflows, carriers, integrations, and volume — there is no fixed plan list. Contact sales: info@thebermuda.us | (512) 428-8740. Details: https://www.thebermuda.us/docs/md/pricing.md

## Rating & Quoting

**What rating APIs are supported?**
TurboRater and Direct Binding, with modular architecture enabling additional quoting engines upon request.

**Can I get quotes for multiple states?**
Yes. Bermuda Rater works in any state the agency operates in — it integrates with the agency's preferred real-time rater and their active carriers. Multi-state quoting is included — pricing is custom and scoped per agency: https://www.thebermuda.us/docs/md/pricing.md

## Integrations

**What CRM integrations are available?**
NowCerts, InsuredMine, FreshWorks, Velocify, InsurancePro, and others. Data flows automatically bidirectionally via webhooks and APIs. Full list: https://www.thebermuda.us/integrations

**Does it support external data prefilling?**
Yes, through Prefill Data API accessing TransUnion, Fenris, DCS, and public records, reducing data entry friction.

**What other integrations are supported?**
Twilio, SendGrid, Google Analytics, Mouseflow, Freshchats, Improvely, Podium, Zapier, Gmail, Google reCAPTCHA, Sentry, BrowserStack, and more. Full list: https://www.thebermuda.us/integrations

**Does it integrate with accounting software?**
Yes — QuickBooks, Microsoft Dynamics GP, Oracle NetSuite. Policy, payment, and report data sync to financial systems.

## Lead Management

**Which real-time lead providers are supported?**
All major real-time lead providers. Leads are automatically fetched, validated, and instantly quoted.

**How does lead integration work?**
Leads are received via secure API or webhook. The platform immediately pre-fills data, runs quotes using configured rating providers, and optionally routes to CRM/AMS.

**Can I customize per lead provider?**
Yes. Each provider has mapping logic, validation rules, workflows, provider-specific filters, enrichments, deduplication rules, and quote handling — all configurable.

**What happens with incomplete lead data?**
The platform supports prefill from TransUnion, Fenris, and public data APIs for auto-completion. Configurable fallback logic flags non-compliant leads.

**Can it auto-respond to leads?**
Yes. Automated responses via SMS (Twilio), email (SendGrid), or webhook to CRM post-quote generation.

## Communication

**What chat tools are compatible?**
Intercom, Freshchat, and Podium integrations enable direct agent interaction on quoting portals.

**Can I customize email settings?**
Yes. SendGrid is fully customizable — From Email Address, From Name, Reply-To Address. Supports branded, authenticated communications.

**Can I use Podium for SMS instead of Twilio?**
Yes. Podium is an alternative for 2-way messaging, lead engagement, and review collection. Selectable during onboarding.

## Automation & Customization

**Does it support workflow automation?**
Yes. Zapier or open Webhook frameworks automate customer creation, quote routing, and notifications. No-code solutions available.

**How customizable is the platform?**
Fully modular and API-first. Integrations are configurable, webhooks customizable, and proprietary systems can connect via the Open Transaction API.

## Technical

**What are the DNS/hosting requirements?**
Domain DNS configuration pointing to Bermuda-hosted portal. Domain authentication for email via SendGrid and live deployment URLs.

**Does it support state-specific configurations?**
Yes. Active states, coverage requirements, zip-code-based routing — all customizable per underwriting preferences.

**What analytics and tracking tools are available?**
Mouseflow provides heatmaps and session recording. Improvely enables conversion tracking and lead attribution analysis. Google Analytics for user activity and conversions.

## More Info

- **Blog:** https://www.thebermuda.us/blog.html
- **Agentic AI:** https://www.thebermuda.us/agentic-ai.html
- **Live Demo:** https://demo.quotes.thebermuda.us
- **Contact:** info@thebermuda.us | (512) 428-8740
