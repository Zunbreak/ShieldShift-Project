# ShieldShift: Vendor-Agnostic Firewall Migration Engine

> **Migrate complex network security policies in seconds, not days.** 
>
> **A CLI & API tool for converting, auditing, and validating firewall configurations between Cisco ASA, FortiGate, and Palo Alto.**



---

## ⚡ The Problem vs. The Solution

**Manual migration:**

* ❌ **Time:** 3–7 days for 500+ rules
* ❌ **Risk:** Human error, shadowed rules, open vulnerabilities
* ❌ **Process:** Excel sheets + manual CLI entry

**With ShieldShift:**

* ✅ **Time:** < 2 minutes (Parse → Convert → Validate)
* ✅ **Precision:** Intermediate Representation (IR) keeps semantics intact between vendors
* ✅ **Security:** Built-in risk analysis and policy auditing

---

## 🚀 Key Features

### 1. True Vendor Independence (IR Engine)

Unlike simple regex scripts, **ShieldShift** parses configs into a standardized **JSON Intermediate Representation**.

* **Input:** Cisco ASA, FortiGate, Palo Alto
* **Output:** Any of the above + JSON (for custom tooling)
* **Benefit:** Add a new vendor parser once, and it automatically unlocks conversions to all other supported vendors.

---

### 2. Built-in Security Audit & Risk Analysis

Don’t just migrate garbage. Clean it up on the way.

* **Detects:** * ANY-ANY-ALLOW style rules
    * Dangerous open ports to private (RFC1918) networks
    * Overly large networks in allow rules
* **Planned extensions (Pro):** * Shadowed rules
    * Unused objects
    * Custom compliance profiles

---

### 3. Data Sovereignty & Anonymization

* **On-Prem execution:** No config data ever leaves your environment.
* **Anonymizer:** Strip sensitive IPs/names so you can safely share configs for troubleshooting, audits, or vendor support.

---

## 🛠 Usage (CLI Examples)

> Note: Command names and flags follow the internal engine; exact syntax may evolve.

```bash
# Convert Cisco ASA config to FortiGate format
shieldshift convert --from cisco_asa --to fortigate ./legacy_fw.cfg --output ./new_fw.conf

# Import config to IR (JSON) for analysis
shieldshift import --type palo_alto ./pa_config.conf --out policy.json

# Run a security risk analysis
shieldshift risk policy.json

# Validate policy (structure & basic consistency)
shieldshift validate policy.json

# Get policy statistics
shieldshift stats policy.json

# Anonymize config for safe sharing
shieldshift anonymize policy.json --out policy_anon.json

# Compare two policies
shieldshift diff policy_old.json policy_new.json


📦 Installation (for licensed product)
⚠️ Important: This repository (ShieldShift-Project) contains documentation, examples and architecture.

The actual engine source code is proprietary and hosted in a private repository.

The commands below describe how installation looks for customers or collaborators,
with access to the private engine repo.

## 📦 Installation (for licensed product)


🔒 Clone the private engine repository below (requires access/license)
```
https://github.com/Zunbreak/ShieldShift.git

```
```
### Installation
cd ShieldShift

# Rest of installation steps create virtual environment
python -m venv .venv

# Linux/macOS:
source .venv/bin/activate

# Windows:
.venv\Scripts\activate

# Install in editable mode
pip install -e .
Once installed, the shieldshift CLI is available on your PATH:

shieldshift --help

🔒 Security & Privacy
🏠 100% On-Prem: All parsing, analysis and conversion is done locally.

🧼 Anonymization-first: Built-in anonymizer makes it safe to share configs externally (support, vendors, audits) without leaking sensitive infrastructure details.

🧾 Designed like a firewall: Decisions are logged, policies are explicit, and defaults are conservative.

🛣️ Roadmap (High-Level)
✅ Core IR models + CLI

✅ Cisco ASA importer/exporter

✅ FortiGate & Palo Alto support (import/export via IR)

✅ Validation, diff, stats, risk analysis

✅ Anonymization (CLI + API)

Planned / in progress:

🔄 Enhanced reporting & risk dashboards (Pro features)

🔄 Web API + minimal web UI (FastAPI-based)

🔄 Additional vendor support (e.g. pfSense, iptables)

🔄 CI/CD integration examples (GitHub Actions)

📄 Ownership & Licensing
ShieldShift is a proprietary software product.

This repository (ShieldShift-Project) is the public documentation and example showcase for the engine.

The core engine source code is maintained privately by Zebastian Larsson (@Zunbreak).

All rights to the ShieldShift engine are reserved. Third-party open source dependencies are used under their respective licenses.

For commercial licensing, enterprise integration, or job inquiries, please contact me directly.

👤 Contact
Author: Zebastian Larsson (@Zunbreak)

📧 Business / licensing: [ShielfShift](shieldshift.business@gmail.com)

💼 LinkedIn: [Zebastian Larsson](https://www.linkedin.com/in/zebastian-larsson-b334861b2/)

🛠 Tech: Python, Typer, FastAPI, IR design, network security tooling
```
