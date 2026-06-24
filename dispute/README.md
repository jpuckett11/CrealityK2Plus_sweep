# Creality Bank Dispute - Public Case File (Sanitized)

**Obsidian Watch Group**
**Date:** 2026-06-17
**Investigator:** Reckoner / Jay Puckett (investigations@obsidianwatch.org)

## What this is

A sanitized copy of a bank-chargeback dispute affidavit and supporting
documentation submitted against Creality (Shenzhen Creality 3D Technology
Co., Ltd.) over an order in which the merchant represented that they
shipped a Creality CR-Scan Otter 3D scanner (~$700 USD) but in fact
shipped only routine 3D printer consumables (a print bed and a small
quantity of replacement nozzles).

Published because:

1. The dispute relied on network-forensic evidence patterns that are
   transferable to other consumers facing similar disputes. The
   sworn-affidavit + mDNS-capture + public-record-context structure is
   a template other Creality customers (or any 3D-printer customer with
   a similar fraud pattern) can adapt for their own bank disputes.
2. Creality's complaint pattern at the Better Business Bureau is a
   matter of public interest. 67 BBB complaints in 3 years, all 67
   unanswered, not BBB-accredited - documented in the affidavit's
   Section 6.
3. The shipping-pattern fraud-indicators documented in Section 5 (three
   packages split across two FedEx + one off-brand courier, with merchant
   tracking opacity) are a forensic playbook other consumers facing
   suspect Creality shipments can use to argue their own disputes.

## What was sanitized

Only the network-device identifiers of the cardholder's 3D printer
(specifically, the K2 Plus's unique model-suffix and the corresponding
mDNS service identifier) are obfuscated with placeholders to prevent
fingerprinting of the residential network. The original signed version
remains in the cardholder's private records and the bank's dispute
file. The case facts, sworn statements, analysis, and conclusions are
otherwise unchanged.

Cardholder name, contact email, and PGP fingerprint are deliberately
retained because they are already public via Obsidian Watch Group's
ordinary research operations.

## Verification

The PGP signature in `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.pdf.asc`
verifies against the published public key for the same fingerprint, and
can be checked by any OpenPGP-compatible tool against
`https://keys.openpgp.org/search?q=investigations@obsidianwatch.org` or
`keyserver.ubuntu.com`.

Verification of the unsanitized original is held by the bank.

## Files in this repository

| File | Description |
|---|---|
| `README.md` | This file |
| `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.md` | Markdown source, original affidavit |
| `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.pdf` | Rendered original affidavit (6 pages) |
| `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.pdf.asc` | Detached PGP signature, original |
| `Creality_Dispute_Supplemental_Affidavit_2026-06-23_SANITIZED.md` | Supplemental affidavit, post-original developments |
| `Creality_Dispute_Supplemental_Affidavit_2026-06-23_SANITIZED.pdf` | Rendered supplemental affidavit |
| `Creality_Dispute_Supplemental_Affidavit_2026-06-23_SANITIZED.pdf.asc` | Detached PGP signature, supplemental |

## 2026-06-23 supplemental affidavit

The 2026-06-23 supplemental affidavit documents the merchant's post-original
conduct including:

1. Creality's redirection of remediation to Seel, Inc. ("Worry-Free Purchase"
   third-party insurance program) during the period of an active bank
   chargeback dispute.
2. Documented public-record Seel claim-handling concerns relevant to the
   bank's evaluation of the redirected pathway, including a Sitejabber-posted
   consumer experience documenting Seel providing a fabricated Venmo
   transaction ID for a refund that did not in fact occur, and BBB / Trustpilot
   complaint patterns including indefinite "under review" status, biometric
   face-scan demands as a precondition for claim adjudication, and a
   documented chargeback collision against Seel directly.
3. Creality's request for direct ACH, wire, or SWIFT transfer information
   outside the original card-network payment rail, and the cardholder's
   declination of that request on standard card-network-refund-handling grounds.
4. The cardholder's assessment that the combination of (1) and (3) during an
   active chargeback period is, in cardholder's experience, consistent with
   coordinated chargeback-defeat conduct rather than genuine remediation.
5. Reaffirmation of the original 2026-06-17 sworn statements and continued
   support for the chargeback dispute.

The supplemental affidavit is structured to be attached to the original in
the bank's dispute file. It does not replace or modify the original.

## License

The case content (sworn statements, factual record, attestations) is
the personal record of the cardholder and is not licensed for
republication as if from another party. The methodology, forensic
analysis pattern, and template structure may be referenced and adapted
by other consumers for their own disputes under a permissive use
arrangement. Cite Obsidian Watch Group if helpful, but the goal here is
that the template is usable.

## Contact

For questions about adapting this pattern to your own dispute:
investigations@obsidianwatch.org

For coordinated reporting on Creality consumer-protection issues:
investigations@obsidianwatch.org

PGP: 9267 A71E 3F0A 4EED 2F97 3F9B A3E2 52F2 4635 CC6C
