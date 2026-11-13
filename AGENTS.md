# Health referral prototype (decision support only)

## Safety (never break these)
- Output is only: REFER NOW, VISIT CLINIC SOON, or MONITOR AT HOME. No diagnosis. No medicine names or doses.
- Every danger sign must exist in docs/protocols.md with a source and page. If it is not there, do not add it. Ask me.
- Synthetic (fake) data only. Never read or write .env or real personal data.
- Phone numbers hidden by default. Revealing one writes an audit entry. CSV exports never contain phone numbers.

## How it works
- flows/triage.json is the single source of questions. USSD, IVR and the web simulators all read it. Never write separate question logic per channel.
- USSD screens max 160 characters. IVR prompts max 28 words (about 10 seconds). Every screen offers 0 = Back. In IVR, * = Repeat.
- Backend: Python FastAPI + SQLite + pytest, in server/. Frontend: reuse the HarvestLink coordinator app in app/.
- Do not invent new visual design. Copy the layout, spacing and components of the nearest existing HarvestLink screen.

## How to work
- Plan first and show me the plan, then code. One task at a time.
- Add a test for every branch. Run tests before saying done.
- Do not scan the whole repo. Open only files you need. Do not edit files I did not mention.
- If you are unsure of an external API (for example Africa's Talking), ask me to approve reading its docs. Do not guess.
- My computer runs Windows PowerShell 5.1: use ; not &&, and Get-ChildItem not ls -la.
- When a task is done, append 3 lines to docs/decisions.md: what is done, what is next, any open problem.