# ShieldShift: Vendor-Agnostic Firewall Migration Engine

> Migrate complex network security policies faster and with fewer mistakes.

ShieldShift är ett proprietärt verktyg för att analysera, konvertera och validera
brandväggskonfigurationer mellan flera plattformar – med fokus på säkra migrationer
och tydlig insyn i vad som faktiskt ändras.

Den här publika repot innehåller **dokumentation och koncept**, inte själva motorn.

---

## Problemet

Manuella migrationer av brandväggsregler är ofta:

- Tidskrävande – dagar eller veckor vid större policies
- Riskabla – mänskliga misstag, skuggade regler, oavsiktligt öppnade portar
- Svåröverskådliga – Excel-ark, diffar i text, olika syntax per vendor

---

## ShieldShift – kortfattat

ShieldShift bygger på en intern **Intermediate Representation (IR)** där
brandväggspolicys normaliseras till ett gemensamt format. Det gör att samma motor kan:

- Läsa konfigurationer från flera olika firewall-vendors
- Göra analyser (statistik, risk, validering)
- Skriva ut motsvarande policy i ett annat vendors format

Exempel på användning (konceptuellt):

```bash
# Konvertera en legacy-policy till ett nytt mål
shieldshift convert --from <vendorA> --to <vendorB> input.conf --out output.conf

# Validera och analysera en policy
shieldshift import --type <vendor> policy.conf --out policy.json
shieldshift validate policy.json
shieldshift risk policy.json
shieldshift diff old_policy.json new_policy.json
