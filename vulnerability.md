# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

to report a vulnerability.

name: "CodeQL Security Scan"
on:
  push:
    branches: [ main, v1.x ]
  pull_request:
    # Analyze PRs targeting these branches
    branches: [ main, v1.x ]

jobs:
  analyze:
    name: Analyze code with CodeQL
    runs-on: ubuntu-latest
    permissions:
      security-events: write
      contents: read

    steps:
      - uses: actions/checkout@v3
      - name: Initialize CodeQL
        uses: github/codeql-action/init@v2
        with:
          languages: python
      - name: Build (if needed)
        run: |
          python3 -m venv .venv
          source .venv/bin/activate
          pip install -r requirements.txt
      - name: Perform CodeQL Analysis
        uses: github/codeql-action/analyze@v2

        	•	Acknowledgment: within 48 hours of receiving a valid report.
	•	Initial triage update: at that 48-hour mark, we’ll let you know whether we’ve reproduced the issue and what priority we’re assigning.
	•	Ongoing status updates:
	•	Weekly for high-severity or critical issues
	•	Bi-weekly for lower-severity issues
	•	Final notification: as soon as a fix is merged (or if we decide to close the report as “won’t fix”), we’ll send you a summary of what was done.

You can of course request more frequent check-ins if you need them, and we’ll do our best to accommodate.
