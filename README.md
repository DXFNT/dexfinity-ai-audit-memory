# Dexfinity AI Ads Audit Memory Pack

**Darček pre Dexfinity tím** — 14 memory súborov z 3 týždňov stavania AI Ads Auditov (Aquapond, Lamely3D, Oxalis, Nebshop a 7 ďalších). Stiahni, importuj do svojho Claude Code, a máš kompletný audit playbook v dosahu.

Tento pack je **audit-špecifický**. Ak potrebuješ len Dexfinity brand foundations (farby, logá, min sizes), pozri `DXFNT/dexfinity-brand-memory`. Pre general UX learnings pozri `DXFNT/dexfinity-ux-memory`.

## Čo v tom je

### 5× Reference (knowledge base)
- **`reference_audit_html_design_system.md`** — master CSS/HTML library (33 KB). CSS variables, sekcie, komponenty, flip cards, pricing, responsive, JavaScript patterns. Gold standard z Aquapond auditu.
- **`reference_audit_product_template.md`** — playbook pre audit produkt: free audit → blurred upsell → flip card payment. Pricing, sales args.
- **`reference_audit_versions.md`** — rozdiel medzi `ai audit` (1 trh, Aquapond) a `ai audit deep` (multi-trh, Lamely3D). Trigger words.
- **`reference_eshop_audit_methodology.md`** — 12-step externý audit proces pre nové eshop leady.
- **`reference_shoptet_premium_design_limits.md`** — čo ide a nejde v Shoptet Premium, breaking changes, checkout limity (používané pri Shoptet eshop auditoch).

### 9× Feedback (pravidlá, ktoré musia byť dodržané)
- `feedback_audit_design_patterns.md` — page structure, colors, flip cards, anti-patterns
- `feedback_audit_double_check.md` — negatívne findings VŽDY overiť 2×
- `feedback_no_overlapping_touch.md` — nikdy neprekrývať interaktívne prvky
- `feedback_no_unsubstantiated_claims.md` — každé číslo musí byť overiteľné
- `feedback_gap_analysis_standard.md` — keyword gap + Google Reviews + human-friendly naming
- `feedback_verify_ads_on_web.md` — vždy navštíviť landing pages pred tvrdeniami
- `feedback_heureka_reviews_audit.md` — Heureka reviews ako social proof v auditoch
- `feedback_gmail_html.md` — drafty pre klienta vždy text/html
- `feedback_gmail_signature.md` — ručne pripojiť signature (pri emaili auditu)

## Ako to importovať do Claude Code

Claude Code udržuje memory v per-project zložke. Máš dve možnosti:

### A) Globálne (odporúčané pre Dexfinity agentov)

Skopíruj obsah memory zložky do globálnej zložky, ktorá sa načítava pri každom projekte:

```bash
# z koreňa tohto repa:
mkdir -p ~/.claude/memory
cp memory/*.md ~/.claude/memory/
```

Ak už máš `~/.claude/memory/MEMORY.md`, **NEPREPISUJ ho** — otvor ho a pridaj riadky z nášho `memory/MEMORY.md` ručne.

### B) Per-project (ak robíš len na jednom Dexfinity projekte)

```bash
# v rámci projektu, kde chceš tieto spomienky použiť:
PROJECT_SLUG=$(pwd | sed 's|/|-|g')
TARGET="$HOME/.claude/projects/$PROJECT_SLUG/memory"
mkdir -p "$TARGET"
cp memory/*.md "$TARGET/"
```

Claude si pri ďalšom spustení v tom projekte načíta tieto súbory automaticky.

### C) One-liner pre rýchly štart

```bash
git clone https://github.com/DXFNT/dexfinity-ai-audit-memory.git
cd dexfinity-ai-audit-memory
mkdir -p ~/.claude/memory
cp memory/*.md ~/.claude/memory/
```

## Čo sa zmení po importe

Tvoj Claude Code bude vedieť:
- **Nasledovať gold-standard štruktúru auditu** (urgency bar → hero → findings → locked → pricing → footer)
- **Rozlíšiť `ai audit` od `ai audit deep`** — trigger words a kedy použiť ktorý
- **Neuveriteľne lepšie kontrolovať fakty** — double-check rule pre negatívne findings, overovanie reklám na webe, žiadne hádanie
- **Zabrániť klasickým audit chybám** — prekrývajúce sa touch targets, zlé flip card CSS, neoverené claims
- **Používať správne finding severity + badge systém** — namiesto semaforov

## Súvisiace packy

- 🎨 **[DXFNT/dexfinity-brand-memory](https://github.com/DXFNT/dexfinity-brand-memory)** — brand foundations (farby, logá, min sizes)
- 🧭 **[DXFNT/dexfinity-ux-memory](https://github.com/DXFNT/dexfinity-ux-memory)** — UX patterns extrahované z reálnych auditov
- 🛠️ **[DXFNT/claude-skills](https://github.com/DXFNT/claude-skills)** — 43 Claude Code skills (install.sh pre rýchle nasadenie)

## Update cyklus

Ak pridávaš nové learnings:
1. Napíš nový `.md` do `memory/` s frontmatter (name, description, type)
2. Pridaj riadok do `memory/MEMORY.md`
3. Commit + push — tím si pri ďalšom `git pull` ťahá update

## Čo v tom ZÁMERNE nie je

- `project_*.md` súbory s klientskymi detailmi — tie ostávajú privátne
- Credentials, API keys, access tokens — žiadne v tomto repe
- Brand-only foundation súbory — tie sú v `dexfinity-brand-memory`

---

**Vyrobil:** Pavol Adámčik + Claude
**Dátum:** 2026-04-23
**Go Beyond.** 🚀
