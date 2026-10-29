A simulated phishing platform for internal security awareness training (like what KnowBe4 or GoPhish does) — crafting training lures, tracking click rates, generating teachable moments for employees who fall for the test
A phishing detection/analysis tool — something that scores inbound emails for phishing indicators (spoofed domains, urgency language, mismatched links, etc.)
A red-team reporting/campaign-management tool for authorized engagements — tracking targets, consent, scope, results
Educational content explaining phishing techniques so people can recognize them
A browser extension or email plugin that flags suspicious messages for end users

Things I won’t help build:

A tool that generates ready-to-send deceptive phishing emails/infrastructure for targeting real people without their knowledge or consent (even “for research”) — that’s the same artifact whether it’s framed defensively or not, and the uplift is identical to building a phishing kit
Credential-harvesting pages, spoofed login portals, or anything designed to actually capture someone’s credentials outside a scoped, consented engagement

So — what’s the actual use case? If this is for an authorized internal phishing simulation program (most common legit version of “AI phishing assistant”), tell me a bit about your setup — in-house security team, specific platform you’re integrating with (GoPhish, KnowBe4, custom), target scale — and I can help you design the AI piece (e.g., an LLM that generates varied, realistic-but-safe training lures based on difficulty level, or one that writes the post-click training explanation).
