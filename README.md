# Aria — AI Inbound Call System
### Built for Arizona In-Home Caregivers

An AI-powered inbound phone system built on VAPI, handling call routing, lead qualification, and SMS follow-up — fully automated, no human agent needed for first contact.

---

## What Was Built

A complete inbound call handling system where **Aria**, the AI voice agent, answers calls, qualifies callers, routes them based on intent, and triggers automated SMS responses — all without a human picking up.

---

## Stack

| Tool | Role |
|------|------|
| **VAPI** | AI voice agent hosting & call handling |
| **Twilio** | Phone number, call routing, SMS delivery |
| **n8n** | Automation backend / webhook triggers |

---

## How It Works

```
Caller dials Twilio number
        ↓
VAPI picks up → Aria introduces herself
        ↓
Aria qualifies the caller (new client / existing / job inquiry)
        ↓
        ├── New client  → collects info, books callback, triggers SMS confirmation
        ├── Existing    → routes to staff line
        └── Job inquiry → collects details, sends info via SMS
```

---

## Agent Design

- **Name:** Aria
- **Persona:** Warm, professional, unhurried — designed to feel human, not robotic
- **Voice:** ElevenLabs via VAPI
- **System prompt:** Structured around intent detection first, then information gathering
- **Interruption handling:** Configured to allow natural conversation flow without cutting callers off

---

##  Call Flows

**Flow 1 — New Client Inquiry**
- Greets caller, detects intent
- Asks qualifying questions (care type, location, urgency)
- Confirms a callback will be arranged
- Fires SMS to caller with next steps

**Flow 2 — Existing Client**
- Recognizes returning caller context
- Warm transfers to the appropriate staff line
- Leaves voicemail trigger if no answer

**Flow 3 — Job / Caregiver Application**
- Collects applicant name, experience, availability
- Sends SMS with application link
- Logs inquiry for follow-up

---

## SMS Automation

Triggered via VAPI → n8n webhook → Twilio SMS.

Each flow sends a context-specific message:
- New client: confirmation + what to expect next
- Job inquiry: application link + timeline

---

## Deliverables (Client-Facing)

- Live VAPI agent (Aria) connected to Twilio number
- 3 configured call flows with distinct routing logic
- SMS automation for each flow
- Full documentation handed to client covering agent settings, how to update prompts, and how to add/remove flows

---

Key Decisions

 **Why VAPI over Bland or Retell?**
VAPI gave the most flexibility for multi-flow routing and webhook integration with n8n at this price point.

**Why n8n for SMS instead of VAPI's native actions?**
More control over message content and timing, and easier to extend later (e.g. logging to a CRM, notifying staff via Slack).

---

 Notes

- Client name anonymized
- API keys and phone numbers removed from all configs
- Prompt structure available on request

---

Built by [Batech](https://batech.framer.website) — AI Automation Specialist
