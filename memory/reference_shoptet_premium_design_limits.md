---
name: Shoptet Premium design limits guide
description: Kompletný overený guide dizajnových limitov Shoptet Premium — čo ide, čo nejde, breaking changes, odporúčania pre dizajnéra, zdroje z developer docs
type: reference
---

Plný dokument: `/Users/pavoladamcak/Documents/Claude/Web a UX/shoptet-premium-design-limits.md`
(kópia aj v: `/Users/pavoladamcak/Documents/Claude/Email NL Forward mailing/shoptet-premium-design-limits.md`)

**Kontext:** Vznikol pre Mamutex e-shop dizajn (detaility / Daniel Čeliga). Overený oproti developers.shoptet.com changelog do Feb 2026.

**Kľúčové fakty:**
- Premium = plná CSS/JS sloboda, ale jadro (checkout, HTML output, produktové limity) sa nemení
- Checkout = 4 fixné kroky, len re-skin
- Max 512 variantov/produkt, 4 varianty, 15 príplatkov — aj v Premium
- Blank šablóna = Classic šablóna bez CSS/JS, nie prázdna stránka
- jQuery vypnuté v blank mode od Jan 2024
- Breaking changes každé 2-6 týždňov, Premium má 2-týždňový buffer (Deferred Template Updates)

**How to apply:** Použiť pri akomkoľvek Shoptet Premium dizajnovom alebo dev rozhodnutí pre Mamutex.
