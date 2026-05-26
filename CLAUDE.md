# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

`oe2-demo` is a standalone HTML prototype/design project for the **Albert Pearlman OE-2** system. It contains interactive UI mockups for new modules being designed before implementation in the main ASP.NET application.

## Project Structure

```
oe2-demo/
├── index.html                      — Module navigation landing page
├── OE2_Proposal_Module_Design.html — Proposal module full UI mockup
├── OCR_Invoice_Module_Design.html  — OCR Invoice automation module design
├── OCR_Invoice_Simple_Design.html  — Simplified OCR Invoice design
└── proposal.jpg                    — Reference image
```

## Running the Demo

No build step. Open any `.html` file directly in a browser:
- Start at `index.html` — links to all module designs
- Each module is self-contained (all CSS/JS inline in the HTML file)

## Design Conventions

All HTML mockup files follow the same structure:
- **Pure HTML/CSS** — no external frameworks, no JavaScript dependencies
- All styles are **inline in `<style>` tags** at the top of each file
- Color palette: Navy `#1e3a5f`, Blue `#2563eb`, light backgrounds `#f0f0f0`
- Font: `Arial, sans-serif`
- Layout: max-width containers, flexbox for workflow steps, table-based form grids

## Modules Included

| File | Module | Status |
|------|--------|--------|
| `OE2_Proposal_Module_Design.html` | Proposal workflow, screens, field layouts | Available |
| `OCR_Invoice_Simple_Design.html` | OCR invoice entry — simple/clean UI | Simple UI |
| `OCR_Invoice_Module_Design.html` | OCR invoice automation — full design | Modern UI |

## Related Implementation Docs

The full implementation spec for the Proposal module (for the ASP.NET app) is at:
`E:\Reliable\OE2-PROPOSALS\document\proposal\IMPLEMENTATION-PROMPT.md`

The actual ASP.NET application being implemented into:
- App path: `E:\Reliable\oe2-demo\WA\` (UI) and `E:\Reliable\oe2-demo\WS\` (Web Service)
- DB: `Data Source=VIJAY_CHAUHAN\SQLEXPRESS;Initial Catalog=OE2;user id=sa;pwd=dingbat`
- Running at: `http://localhost:5054/` (Login: `reliable` / `123`)

## Proposal Module — Key Business Rules (for UI reference)

- **3 proposal types:** New Job/Bidding (`B`), Extra-Unapproved (`P`), Extra-Approved (`O`)
- **Proposal number format:** `YYYYNNNNN` e.g. `202600001`; revision: `202600001-001`
- **Status flow:** Draft → Sent → Converted (for new jobs) | P → O → Billed (for extras)
- **Alternates:** Optional scope items, NOT included in total until selected at Convert-to-Job
- **Group Order:** Multiple O-status extras grouped under one PO# — originals stay, PO# propagates back
- **Clone for GC:** Copy proposal to different GC customer, new proposal number assigned
