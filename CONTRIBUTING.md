# Contributing to RuralConnect

Thank you for your interest in RuralConnect! We're building a solution for rural connectivity challenges, and we need your expertise and perspective.

This document will help you understand how to contribute effectively.

---

## 🎯 What We Need Right Now

### **Phase 1: Customer Discovery (May - June 2026)**
We're validating the problem and product-market fit. If you can help:

- **Field Research:** 
  - Talk to rural communities about connectivity gaps
  - Share data on signal patterns in your region
  - Document real-world use cases (farming, education, health)
  - **How to contribute:** Open an issue under `research/` or email founders@ruralconnect.io

- **Market Research:**
  - Analyze competitor solutions (JioAirFiber, satellite providers, dual-SIM phones)
  - Research pricing sensitivity in rural India/Africa/Southeast Asia
  - Study telecom regulations in target markets
  - **How to contribute:** Add to `docs/competitive_analysis.md` via PR

---

### **Phase 2: Bench Prototype (June - July 2026)**
Building and testing the core hardware + software logic.

- **Embedded Systems Engineers:**
  - Review hardware schematic for Quectel RM500Q-GL integration
  - Test Raspberry Pi Zero 2W + modem performance under load
  - Optimize eSIM switching latency
  - **How to contribute:** Comment on issues tagged `hardware` or `firmware`

- **Linux/Python Developers:**
  - Develop the network switching daemon (`firmware/network_daemon.py`)
  - Build the OLED display UI (`firmware/display_ui.py`)
  - Create Flask config web interface (`firmware/web_ui.py`)
  - Write unit tests for network scoring algorithm
  - **How to contribute:** Fork and submit PR against `develop` branch (create if needed)

- **DevOps/System Engineers:**
  - Set up CI/CD pipeline for firmware testing
  - Create Raspberry Pi OS image builder
  - Document reproducible build steps
  - **How to contribute:** Open an issue with setup proposal

---

### **Phase 3: Field Testing (August - September 2026)**
Testing with real rural users and iterating.

- **Field Testers:**
  - Deploy prototype in rural areas and document signal behavior
  - Test battery life, switching time, Wi-Fi stability
  - Gather user feedback on UX (display, config interface)
  - **How to contribute:** Share findings in `research/field_test_logs/`

- **QA/Testing:**
  - Create test plans for modem switching scenarios
  - Document edge cases (no signal, weak signal, carrier unavailable)
  - Stress-test with multiple Wi-Fi clients
  - **How to contribute:** Add to `docs/test_plan.md`

---

## 📋 How to Contribute

### **1. Start with Issues**
- Check [open issues](../../issues) to see what's needed
- Issues are tagged: `hardware`, `firmware`, `research`, `documentation`, `help-wanted`, `good-first-issue`
- Comment on issues you're interested in — we'll assign it to you

### **2. Fork & Create a Branch**
```bash
git clone https://github.com/YOUR_USERNAME/Ruralconnect.git
cd Ruralconnect
git checkout -b feature/your-feature-name
```

**Branch naming:**
- `research/field-notes-bihar` (research findings)
- `feature/network-switching-daemon` (new feature)
- `fix/esim-switch-latency` (bug fix)
- `docs/competitive-analysis` (documentation)

### **3. Make Your Changes**
- Keep commits atomic and descriptive
- Add docstrings to code
- Update README if adding new directories/components
- Reference the issue number in commit messages (e.g., `Fixes #15: Implement network scoring`)

### **4. Submit a Pull Request**
- Link to the issue you're addressing
- Describe what you changed and why
- If adding code, include test results
- If adding research, cite sources

**PR Template:**
```
## Issue
Closes #<issue-number>

## Changes
- [ ] What you changed
- [ ] Why you changed it

## Testing
- [ ] How you tested this
- [ ] Any edge cases considered

## Notes
Any additional context?
```

---

## 📁 Repository Structure & Guidelines

```
RuralConnect/
├── README.md                               ← Project overview
├── CONTRIBUTING.md                         ← This file
├── docs/
│   ├── RuralConnect_Tech_Spec.md          (convert .docx to .md)
│   ├── RuralConnect_Business_Plan.md      (convert .docx to .md)
│   ├── competitive_analysis.md            ← Competitor research
│   ├── test_plan.md                       ← QA test scenarios
│   └── regulatory_roadmap.md              ← BIS/FCC/etc. requirements
├── hardware/
│   ├── BOM.md                             ← Bill of Materials with supplier links
│   ├── schematics/                        ← KiCAD/Fritzing files
│   ├── enclosure/                         ← 3D STL files for IP65 box
│   └── assembly_guide.md                  ← Step-by-step assembly
├── firmware/
│   ├── network_daemon.py                  ← Core switching logic
│   ├── display_ui.py                      ← OLED display control
│   ├── web_ui.py                          ← Flask config interface
│   ├── tests/                             ← Unit tests
│   ├── requirements.txt                   ← Python dependencies
│   └── README.md                          ← Build & deploy instructions
├── research/
│   ├── field_test_logs/                   ← Real-world testing notes
│   ├── customer_interviews/               ← Anonymized user feedback
│   ├── signal_measurements/               ← Regional signal data
│   └── market_research/                   ← Competitive & regulatory notes
└── .github/
    ├── ISSUE_TEMPLATE/
    │   ├── bug_report.md
    │   ├── feature_request.md
    │   └── research_task.md
    └── PULL_REQUEST_TEMPLATE.md
```

---

## 💻 Development Setup

### **For Firmware Developers**
```bash
# Clone and set up environment
git clone https://github.com/YOUR_USERNAME/Ruralconnect.git
cd Ruralconnect/firmware

# Create virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run tests
python -m pytest tests/

# Run locally (requires Raspberry Pi or simulator)
python network_daemon.py --dry-run
```

### **For Hardware/Documentation Contributors**
- No special setup needed
- Use Markdown for all `.md` files
- For schematics: Use KiCAD (free, open-source) or Fritzing
- For 3D enclosure: Use Fusion 360 (free tier) or FreeCAD

---

## 🐛 Reporting Issues

### **Bug Report**
Use the [bug report template](../.github/ISSUE_TEMPLATE/bug_report.md):
- What you were doing
- What happened vs. what you expected
- Steps to reproduce
- Environment (OS, Raspberry Pi model, Python version, etc.)

### **Feature Request**
Use the [feature request template](../.github/ISSUE_TEMPLATE/feature_request.md):
- Problem you're trying to solve
- Proposed solution
- Why it matters (especially for rural users)

### **Research Task**
Use the [research task template](../.github/ISSUE_TEMPLATE/research_task.md):
- What needs to be researched
- Where to find information
- Expected output format

---

## 🤝 Code of Conduct

- Be respectful and inclusive — we're a global, distributed team
- Focus on the problem, not personalities
- Credit others' ideas and work
- If you see harassment, report it privately to founders@ruralconnect.io

---

## 📊 Recognition

All contributors will be:
- Added to the project README under "Contributors"
- Credited in release notes
- Invited to the team Slack/Discord (when established)
- Eligible for advisory positions in a future non-profit or social enterprise

---

## 🙋 Questions?

- **GitHub Issues:** For project-specific questions
- **Email:** founders@ruralconnect.io
- **Want to discuss before coding?** Open a [GitHub Discussion](../../discussions) or ask in an issue

---

## 📝 License & IP

This project is currently **All Rights Reserved** pending patent filing. By contributing, you agree that:
- Your contributions may be included in the final product
- You're comfortable with future licensing (likely open-source post-patent)
- You'll be credited appropriately

Questions about licensing? Email founders@ruralconnect.io

---

**Thank you for helping RuralConnect reach rural communities! 🌾📡**
