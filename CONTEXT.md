# Enterprise Control Centre — Context

**Updated:** 28 October 2026  
**Working folder:** `Desktop/Agentic Enterprise God's Eye/`  
**Context mirror:** `Desktop/CC/Context/enterprise-control-centre/`

---

## What we are trying to do

Build a **DigiConsent / Consent OS Enterprise Control Centre** for **telco investigators**: a portal where they explore an enterprise’s brands → lines of business → templates/assets, open **concerns** (UC1/2/3/4/6/9), and run **simulated** Investigator → Approver enforcement (Stories A–C).

This is a **demo / prototype**, not production. Enforcement is visibly simulated. There is **no Trust score** (no guilt-by-score framing).

**Primary demo enterprise:** Aster Finance (`PE-ASTER`).

**North-star visual (current direction):** a light **operations campus** UI — isometric floor plan, blue concern routes, one floating concern card when focused, dense right inspector — inspired by a facility/AGV “Operations” dashboard reference (not a warehouse product; DigiConsent domain content).

---

## Product rules (locked)

| Topic | Decision |
|---|---|
| Shape | Portal shell; single-file HTML prototypes |
| Data | Deterministic in-file fixtures (Aster enriched) |
| Roles | Investigator **proposes** → Approver **confirms** → simulated apply |
| Demo C | Restrict T101/T204/T310 → partly applied **2 of 3** (T310 fails) → retry |
| UC1 | Loan-offer templates mapped to Savings; exposure **1,100**; T204 idle = 0; Savings consents preserved; no remap |
| Trust score | Never shown |
| Trust Map original | Keep untouched as visual reference |

**Six UCs:** navigable. **Stories A–C:** fully actionable (simulated). UC3/UC4/UC6/UC9 evidence-limited where needed.

---

## What we did (session arc)

### 1. First ECC build (dark / Trust Map lineage)

- Extended Trust Map patterns into **`Enterprise_Control_Centre.html`**.
- Chrome rename to Control Centre, Investigator \| Approver, Aster fixtures, Insights dock language, six UCs, Demo A–C actions.
- Viz experiments on the stage: isometric buildings → abstract “god’s eye” → collapsible tidy **tree** (Enterprise → Brands → LOBs → Assets).
- Tree had runtime bugs (SVG nodes classed as directory `.tcard`; collapsed LOBs crashed `stubB3` on null `_p`). Those were fixed in the tree file; tree remains a **legacy exploration**.

### 2. Ops campus reboot (current v1)

User shared an **Operations** dashboard reference (light chrome, isometric blocks, blue routes, floating cards, floating inspector). Decisions:

| Choice | Pick |
|---|---|
| Floor metaphor | **Hybrid** — campus default; selecting a concern highlights route + inspector |
| Theme | **Light ops** (match reference) |
| Codebase | **New file** `Enterprise_Control_Centre_Ops.html` (do not mutate Trust Map / old ECC) |
| Scope | Full Demo A–C |

Built Ops prototype:

- Light top bar, search, role switch, floating **inspector** over the map.
- True **isometric** campus (white prisms, diamond grid, decorative racks).
- Brands / LOBs / templates as 3D pads; blue **routes with nodes** when a concern is focused.
- Concern **pins** on overview; **one floating card only when that concern is in focus** (not all cards open).
- Aster fixtures + propose / Approver confirm / partial apply / retry.

### 3. Fidelity pass (in progress)

User feedback: dimensions/layout must match the reference more closely; cards must not all be open. Addressed focus-only cards and campus spacing; further visual polish (route density, card chrome, block proportions) may still be needed to hit reference fidelity.

---

## Files that matter

| File | Role |
|---|---|
| **`Enterprise_Control_Centre_Ops.html`** | **Current v1** — light isometric ops campus + A–C |
| `Enterprise_Control_Centre.html` | Earlier dark / tree ECC (kept) |
| `Enterprise_Trust_Map_4.html` (+ copy) | Original isometric Trust Map (untouched reference) |
| `theme-choice.html` | Temporary A/B/C theme picker from brainstorm |
| `README.md` | How to open / demo path |
| `docs/superpowers/specs/2026-10-28-enterprise-control-centre-design.md` | Original ECC design spec |
| `docs/superpowers/specs/2026-10-28-enterprise-control-centre-ops-design.md` | Ops campus decisions |
| `scripts/verify-fixtures.mjs` | Fixture checks (Aster / ECC data) |
| `CONTEXT.md` | This file |

---

## Demo path (Ops — Stories A–C)

1. Open `Enterprise_Control_Centre_Ops.html` → **Aster Finance**.
2. Campus overview: pins for open concerns; inspector shows situation + priority list. **No floating card yet.**
3. Click a pin or **UC1** row → one card + blue route (Bank → Savings → T101/T204/T310).
4. **Review action** → propose restrict (Investigator) → toast to switch role.
5. **Approver** → Confirm simulated apply → **Partly applied 2 of 3** (T310 failed).
6. Retry failed target or close monitoring.

---

## Aster map ontology (short)

- **Aster Bank** — Savings (L-SAV), Loans (L-LOAN), Cards  
- **Aster Finance Offers** — Financial Offers (L-FINOFF)  
- **Aster Verify** — Verification / KYC  

UC1 spine templates: **T101, T204 (idle), T310** confirmed; **T400, T405, T410** cleared for that finding.

---

## What we are still trying to do

1. **Raise Ops visual fidelity** to the shared Operations reference (isometric proportions, card layout, inspector density, route feel) without losing DigiConsent content or A–C behaviour.
2. Keep **one-card-on-focus** behaviour; overview = pins + inspector list only.
3. Optionally polish Ask / walk-through / registry of quieter enterprises if needed for the pitch.
4. Keep Trust Map + tree ECC as references; **Ops file is the active demo surface** unless product says otherwise.
5. Mirror important docs into `CC/Context/enterprise-control-centre/` for other chats.

---

## How to talk about this in a new chat

> We’re building DigiConsent Enterprise Control Centre for telco investigators. Active file is `Enterprise_Control_Centre_Ops.html`: light isometric ops campus, hybrid concern routes, Investigator/Approver simulated A–C on Aster Finance. No Trust score. See `CONTEXT.md` and the Ops design spec. Don’t overwrite `Enterprise_Trust_Map_4.html`.
