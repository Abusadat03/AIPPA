A simulated phishing platform for internal security awareness training (like what KnowBe4 or GoPhish does) — crafting training lures, tracking click rates, generating teachable moments for employees who fall for the test
A phishing detection/analysis tool — something that scores inbound emails for phishing indicators (spoofed domains, urgency language, mismatched links, etc.)
A red-team reporting/campaign-management tool for authorized engagements — tracking targets, consent, scope, results
Educational content explaining phishing techniques so people can recognize them
A browser extension or email plugin that flags suspicious messages for end users

Things I won’t help build:

A tool that generates ready-to-send deceptive phishing emails/infrastructure for targeting real people without their knowledge or consent (even “for research”) — that’s the same artifact whether it’s framed defensively or not, and the uplift is identical to building a phishing kit
Credential-harvesting pages, spoofed login portals, or anything designed to actually capture someone’s credentials outside a scoped, consented engagement

So — what’s the actual use case? If this is for an authorized internal phishing simulation program (most common legit version of “AI phishing assistant”), tell me a bit about your setup — in-house security team, specific platform you’re integrating with (GoPhish, KnowBe4, custom), target scale — and I can help you design the AI piece (e.g., an LLM that generates varied, realistic-but-safe training lures based on difficulty level, or one that writes the post-click training explanation).
Enterprise architecture

Ingestion layer

Integrates with mail gateways (Microsoft 365/Exchange Online, Google Workspace) via API — Microsoft Graph API, Gmail API — to scan mail pre- or post-delivery
Needs to handle volume: large orgs can see millions of emails/day, so this has to be async/queued, not synchronous LLM calls on every message

Multi-stage detection pipeline (cheap-to-expensive, to control cost)

Fast rules/heuristics pass (SPF/DKIM/DMARC, domain reputation, known-bad URL/IP lists) — filters out the obvious majority
ML classifier (trained on labeled phishing/ham corpus) — catches statistical patterns
LLM pass only on the ambiguous middle tier — semantic analysis of intent, impersonation, urgency, context (e.g., “is this plausible given the sender’s actual role and the recipient’s job function?”)

Org-aware context — this is what separates enterprise from individual tools:

VIP/exec impersonation detection (BEC attacks often spoof the CEO/CFO)
Vendor/supply-chain email compromise detection (watching for compromised partner accounts)
Integration with identity provider (Okta/Azure AD) to know who’s actually who, and who should be emailing whom

SOC-facing tooling

Case management, campaign clustering (grouping related phishing attempts hitting multiple employees so analysts see the whole wave, not isolated tickets)
SIEM/SOAR integration (Splunk, Sentinel, etc.) for automated response playbooks — auto-quarantine, force password reset, alert affected users

Feedback loop

User-reported phishing button feeds back into retraining
False-positive review queue (critical — overly aggressive flagging erodes trust fast)
