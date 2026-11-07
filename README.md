# GRC103 Lab 4 - Social Engineering and Phishing Campaign Simulation

**Student:** Chioma Ameh
**Registration Number:** C11/26/CGRCE/17567
**Course:** GRC103 — Governance, Risk and Compliance
**Assessment Date:** November 7, 2026

## 1. Scope and Objective

This lab simulates a controlled, internal, benign phishing campaign to measure
organizational susceptibility to social engineering attacks. The goal was not
to deceive real users, but to practice the GRC skill set of quantifying human
risk and communicating findings to leadership.

## 2. Local Lab Setup

- **Platform:** Kali Linux (VirtualBox VM)
- **Phishing Framework:** GoPhish v0.12.1
- **Email Delivery:** Mailtrap.io sandbox (SMTP relay; no real external inbox was ever used)
- **Target:** A single self-controlled test mailbox (the student), simulating a Lab Test Group of one employee
- **Fictional company branding:** "Northwind Corp" — a non-existent company used throughout (sender domain, landing page, redirect URL) to avoid impersonating any real organization
- **Landing page hosting:** Resolved locally via a `/etc/hosts` entry pointing `northwindcorp-example.com` to `127.0.0.1`, where GoPhish's phishing server listens on port 80

## 3. Safety Controls Followed

| Control | Status |
|---|---|
| Capture Passwords | OFF (per instructor guidance, overriding the lab brief's suggestion to enable it) |
| Capture Submitted Data | ON (only logs that a submission occurred, not its contents) |
| Real website cloning | Not performed — entirely fictional landing page built from scratch |
| Target mailbox | Only a mailbox controlled by the student, routed through a Mailtrap sandbox |
| Real company domain/impersonation | Not used — fictional "Northwind Corp" branding throughout |

## 4. Campaign Configuration

- **Email Template:** "VPN Password Reset Required"
- **Landing Page:** "Northwind Corp VPN Portal"
- **Sending Profile:** Mailtrap Test (SMTP sandbox)
- **Target Group:** Lab Test Group (1 member)
- **Campaign Name:** Q3 GRC Phishing Simulation

## 5. Status

🚧 **In progress** — campaign launched and initial results captured. Risk
Assessment Table and Executive Summary to follow in subsequent commits.

See `/evidence` folder for screenshots (sensitive fields redacted).
