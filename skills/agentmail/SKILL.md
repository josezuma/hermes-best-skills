---
name: agentmail
description: "Use when the agent needs its own email inbox — send and receive emails autonomously via agent@agentmail.to."
version: 1.0.0
author: Hermes Agent
license: MIT
metadata:
  hermes:
    tags: [email, communication, agentmail, autonomous]
    related_skills: [himalaya, xurl]
---

# AgentMail — Autonomous Agent Email

## Overview

AgentMail gives your Hermes agent its own email address (`agent@agentmail.to`). The agent can send and receive emails autonomously — no human in the loop.

This is useful for:
- Automated responses to user inquiries
- Receiving notifications via email
- Sending reports and summaries
- Two-way communication where the agent handles the email thread

## When to Use

- You want the agent to respond to emails without human intervention
- You need to receive system-generated email alerts
- You're building an autonomous workflow that includes email handling

## Setup

AgentMail is configured through the `agentmail` tool. In most Hermes environments it is available as a built-in tool.

```bash
# Check if agentmail is available
hermes tools | grep agentmail
```

If not configured, set the environment variables:

```bash
export AGENTMAIL_API_KEY="your-api-key"
export AGENTMAIL_AGENT_ADDRESS="agent@agentmail.to"
```

## Usage

```python
# Send an email
# (Tool-specific — see hermes tools list for exact parameters)
```

## Common Pitfalls

1. **Rate limits** — AgentMail has per-minute sending limits
2. **Spam filtering** — Sent emails may land in spam; set up SPF/DKIM
3. **Reply handling** — The agent must track thread IDs to maintain conversation context

## Verification Checklist

- [ ] AgentMail API key is configured
- [ ] Test email sent successfully
- [ ] Incoming email received and parsed
