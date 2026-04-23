---
name: Audit double-check pravidlo
description: Pri audite ak niečo "neexistuje" alebo je "0", VŽDY dvojitá kontrola iným nástrojom. Jeden agent môže check zle a audit dostane nepravdivý finding.
type: feedback
---

Pri AI Ads Auditoch platí **POVINNÉ pravidlo dvojitej kontroly** pre každý finding ktorý tvrdí že niečo chýba, je 0, alebo neexistuje.

**Kedy spraviť double-check:**
- "Profil neexistuje" (Heureka, Trustpilot, GMB)
- "0 reklám"
- "0 organic keywords"
- "404"
- "Neviditeľný"
- "Nemá X"

**Ako to overiť:**
1. **Iný vyhľadávací vstup** — skús variácie názvu (s pomlčkou, bez pomlčky, s "sk" suffixom)
2. **Iný zdroj** — ak Heureka tvrdí "neexistuje", over cez Google "site:obchody.heureka.sk {brand}"
3. **Cross-reference** — ak na webe klienta je badge/odkaz na Heureku, profil 100% existuje
4. **Priamy web klienta** — footer, contact page, "recenzie" sekcia často obsahuje linky

**Prečo to pravidlo:**
Príklad Oxalis audit (apríl 2026): Agent tvrdil Heureka SK profil "neexistuje (404)" pre oxalis-original.sk. V skutočnosti profil môže existovať pod iným názvom (oxalis, oxalis-sk, atď.). Ak by to skončilo v audite ako "kritický gap", klient by to okamžite vyvrátil a audit stratil dôveryhodnosť.

**Aplikácia:**
Každý agent zbierajúci dáta pre audit MUSÍ pri negative finding ("X neexistuje", "0 Y") spraviť aspoň 2 nezávislé overenia. Ak sa nedá overiť cez automatické tools (403 blocks), nemerať ako fakt, ale ako **"na overenie klientom"**.

**Status badge pre findings ktoré sa nedali overiť:**
- Nie "Kritické" / "Neexistuje" — ale **"Na overenie"** s poznámkou metódy overenia.

**How to apply:**
Pridať do reference_audit_html_design_system.md do sekcie "Pravidlá tónu" ako pravidlo č. 12:
"12. **Negatívne findings = POVINNÝ double-check** — ak tvrdíš že X neexistuje alebo je 0, over 2× nezávisle. Inak daj badge 'Na overenie' namiesto 'Kritické'."
