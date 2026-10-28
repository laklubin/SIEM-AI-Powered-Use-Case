# AI-Powered Attack & Detection — SIEM Use Case Library

90 SIEM detection use cases for attacks in which **AI is the weapon**, not the target.

This is the companion to [AI Security Use Cases](https://laklubin.github.io/AI-Security-Use-Case-SIEM/) (MITRE ATLAS + OWASP LLM Top 10), which covers attacks *against* AI systems. This library points the other way: generated phishing and deepfakes, autonomous agent intrusion, adversarial evasion of security ML, shadow-AI data loss, and abuse of the LLM and model-supply-chain estate.

Every use case carries three fields, as well as a detection note and an indicative framework mapping:

- **Use case name** — what you are detecting
- **Log source** — the specific telemetry it is detectable in
- **Sample log** — an illustrative log line showing the field names and discriminating values

Live site: https://laklubin.github.io/SIEM-AI-Powered-Use-Case/

## Categories

| # | Category | Focus |
|---|---|---|
| 8 | AI-Generated Phishing & BEC | Mass-personalised lures, thread hijack, quishing, AI-cloned portals |
| 8 | Deepfake & Synthetic Identity | Video/voice impersonation, KYC and voice-biometric defeat, interview fraud |
| 8 | AI-Assisted Reconnaissance & OSINT | Agentic crawling, attack-surface discovery, dossier building |
| 8 | AI-Generated Malware & Polymorphic Payloads | Per-victim payloads, LLM-authored scripts, tuned sandbox evasion |
| 10 | Agentic & Autonomous Attack Operations | Autonomous exploit loops, MCP tool abuse, indirect prompt injection, agent pacing |
| 8 | AI-Powered Credential & Access Attacks | ML-guided spraying, CAPTCHA defeat, adaptive MFA fatigue, fingerprint rotation |
| 8 | Adversarial Evasion of Security ML | Classifier perturbation, natural-language DGA, UEBA baseline poisoning |
| 10 | Shadow AI & GenAI Data Exfiltration | Prompt-body exfiltration, unsanctioned tools, over-scoped OAuth, lookalike endpoints |
| 9 | LLM & Agent Infrastructure Abuse | Key theft, denial-of-wallet, jailbreak campaigns, vector-store scraping |
| 8 | AI Supply Chain & Model Integrity | Unvetted weights, pickle execution, typosquats, poisoned training data |
| 5 | Defensive AI & SOC Tooling Integrity | Injection via log fields, AI auto-close abuse, detection-as-code tampering |

Severity spread: 28 Critical · 46 High · 16 Medium. 89 distinct log sources across 12 log families (email, identity, endpoint, network, cloud audit, AI gateway, ML platform, CI/CD, voice/video, DLP, SIEM tooling, threat intel).

## Files

- `index.html` — the published, filterable use case library (GitHub Pages)
- `usecases.json` — the structured dataset behind it

## Dataset schema

```json
{
  "id": "AIPA-001",
  "name": "LLM-generated spear-phish from newly registered lookalike domain",
  "category": "AI-Generated Phishing & BEC",
  "log_family": "Email & Collaboration",
  "severity": "High",
  "mitre": ["T1566.001", "AML.T0052"],
  "description": "...",
  "log_source": "Microsoft 365 Defender — EmailEvents / Exchange Online message trace",
  "sample_log": "EmailEvents | ts=... SenderDomainAge=11d ...",
  "detection": "Correlate sender domain age (< 30 days) with SPF/DKIM pass and DMARC absent..."
}
```

## Caveats

**Sample logs are synthetic.** Every log line was written by hand to illustrate the field names, shape and discriminating values an analyst should look for in that source. They are not captured telemetry and not vendor-published samples, and field names vary by product version and configuration — validate against your own schema before building content from them. Hostnames, accounts and domains are fictional; IP addresses use the RFC 5737 documentation ranges or RFC 1918 private space.

**Framework mappings are indicative.** ATT&CK and ATLAS technique IDs are analyst-assigned for orientation, not certified mappings — neither framework publishes a taxonomy for AI-as-the-weapon tradecraft, which is the gap this library fills. Severity is a scoping judgement, not a risk rating for your environment.

Sources and further reading: [MITRE ATT&CK](https://attack.mitre.org) · [MITRE ATLAS](https://atlas.mitre.org) · [OWASP GenAI Security Project](https://genai.owasp.org)

Maintained by LK for detection engineering and AI assurance reference.
