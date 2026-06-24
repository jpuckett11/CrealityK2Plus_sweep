# Creality Bank Dispute - Public Case File (Sanitized)

**Obsidian Watch Group**
**Original date:** 2026-06-17 (original affidavit)
**Latest correction:** 2026-06-24 (second supplemental affidavit)
**Investigator:** Reckoner / Jay Puckett (investigations@obsidianwatch.org)

## What this is

A sanitized copy of a bank-chargeback dispute affidavit set and
supporting documentation submitted against Creality (Shenzhen Creality
3D Technology Co., Ltd.) over an order in which the merchant represented
that they shipped a Creality CR-Scan Otter 3D scanner (approximately
$700 USD) plus an associated print bed and replacement heater-nozzle
assemblies via an off-brand carrier (SpeedX, tracking
SPXBNA007982605180000011), and the cardholder did not receive the
package. The merchant's representation of delivery is physically
inconsistent with the cardholder's gated property layout and is the
subject of the active chargeback dispute.

Published because:

1. The dispute relied on network-forensic evidence patterns that are
   transferable to other consumers facing similar disputes. The
   sworn-affidavit + mDNS-capture + public-record-context structure is
   a template other Creality customers (or any 3D-printer customer with
   a similar pattern) can adapt for their own bank disputes.
2. Creality's complaint pattern at the Better Business Bureau is a
   matter of public interest. 67 BBB complaints in 3 years, all 67
   unanswered, not BBB-accredited - documented in the original
   affidavit's Section 6.
3. The shipping-pattern carrier-selection observation (high-value
   disputed item routed through SpeedX with weak proof-of-delivery
   infrastructure; lower-individual-value items routed through FedEx
   with strong proof-of-delivery infrastructure) is a forensic
   indicator pattern other consumers facing suspect Creality shipments
   can use to argue their own disputes.
4. The proactive-correction posture in the 2026-06-24 second
   supplemental affidavit is the OWG-standard methodology for
   handling sworn-statement corrections. Other investigators and
   consumers facing similar situations can use the second
   supplemental as a template for how to correct sworn statements
   transparently without weakening the underlying dispute.

## What was sanitized

Only the network-device identifiers of the cardholder's 3D printer
(specifically, the K2 Plus's unique model-suffix and the corresponding
mDNS service identifier) are obfuscated with placeholders to prevent
fingerprinting of the residential network. The original signed
unsanitized versions remain in the cardholder's private records and
the bank's dispute file. The case facts, sworn statements, analysis,
and conclusions are otherwise unchanged.

Cardholder name, contact email, and PGP fingerprint are deliberately
retained because they are already public via Obsidian Watch Group's
ordinary research operations.

## Verification

The PGP signatures in the `.pdf.asc` detached-signature files verify
against the published public key for the cardholder's fingerprint, and
can be checked by any OpenPGP-compatible tool against
`https://keys.openpgp.org/search?q=investigations@obsidianwatch.org`
or `keyserver.ubuntu.com`.

Verification of the unsanitized originals is held by the bank.

## Files in this repository

| File | Description |
|---|---|
| `README.md` | This file |
| `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.md` | Markdown source, original affidavit |
| `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.pdf` | Rendered original affidavit |
| `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.pdf.asc` | Detached PGP signature, original |
| `Creality_Dispute_Supplemental_Affidavit_2026-06-23_SANITIZED.md` | First supplemental (Seel redirection, ACH/wire request) |
| `Creality_Dispute_Supplemental_Affidavit_2026-06-23_SANITIZED.pdf` | Rendered first supplemental |
| `Creality_Dispute_Supplemental_Affidavit_2026-06-23_SANITIZED.pdf.asc` | Detached PGP signature, first supplemental |
| `Creality_Dispute_Second_Supplemental_Affidavit_2026-06-24_SANITIZED.md` | Second supplemental (correcting original §2; SpeedX carrier; gated-property delivery account; shifted merchant delivery account) |
| `Creality_Dispute_Second_Supplemental_Affidavit_2026-06-24_SANITIZED.pdf` | Rendered second supplemental |
| `Creality_Dispute_Second_Supplemental_Affidavit_2026-06-24_SANITIZED.pdf.asc` | Detached PGP signature, second supplemental |
| `Affirm_Investigator_Briefing_2026-06-24.md` | Briefing for Affirm investigator on BNPL-lender prejudice pattern |
| `Affirm_Investigator_Briefing_2026-06-24.pdf` | Rendered Affirm briefing |
| `Affirm_Investigator_Briefing_2026-06-24.pdf.asc` | Detached PGP signature, Affirm briefing |

## 2026-06-24 second supplemental affidavit

The second supplemental affidavit corrects, transparently and on the
record, factual statements in the original 2026-06-17 affidavit's §2
("What was actually received"). The accurate factual record:

1. **The order included multiple items** shipped across three packages:
   the Creality K2 Plus 3D printer, the Creality CFS (Creality Filament
   System) module, the Creality CR-Scan Otter 3D scanner, the 3D
   printer build plate, and replacement heater-nozzle assemblies.
2. **Packages 1 and 2 (FedEx)** contained the K2 Plus printer and the
   CFS module respectively. Both received and accepted by the
   cardholder.
3. **Package 3 (SpeedX, tracking SPXBNA007982605180000011)** was
   represented to contain the CR-Scan Otter scanner, the bed, and the
   nozzles. Not received by the cardholder.
4. **The SpeedX tracking record states "delivered to front door"** on
   21 May 2026 at 14:17. The cardholder's residence is fully fenced
   and gated; the front door is not accessible to the public without
   passage through the gated perimeter. The SpeedX claim is physically
   inconsistent with the property layout.
5. **The merchant subsequently modified the delivery account** to
   assert that the package had been placed in the driveway (outside
   the gate), after the cardholder pointed out the gate situation.
   The modified account is not supported by any contemporaneous
   carrier record and is inconsistent with the SpeedX tracking record
   on which the merchant relies for the underlying claim of delivery.
6. **The chargeback dispute is limited to Package 3 contents only**
   (the Otter scanner, the bed, the nozzles). The cardholder does not
   dispute the portions of the purchase corresponding to Packages 1
   and 2 (the printer and the CFS module), which were received and
   accepted.
7. **The merchant's carrier selection** routed the high-value
   disputed item (the CR-Scan Otter scanner, approximately $700
   retail) through SpeedX (an off-brand e-commerce delivery service
   with weaker proof-of-delivery infrastructure) while routing the
   other items through FedEx (strong proof-of-delivery
   infrastructure). This asymmetry is forensically inconsistent with
   normal merchant fulfillment practice for a high-value item.

All sworn statements in the 2026-06-17 original affidavit and the
2026-06-23 first supplemental affidavit remain in effect except as
specifically corrected in the 2026-06-24 second supplemental.

## 2026-06-23 first supplemental affidavit

The first supplemental affidavit documents the merchant's
post-original conduct including:

1. Creality's redirection of remediation to Seel, Inc. ("Worry-Free
   Purchase" third-party insurance program) during the period of an
   active bank chargeback dispute.
2. Documented public-record Seel claim-handling concerns relevant to
   the bank's evaluation of the redirected pathway, including a
   Sitejabber-posted consumer experience documenting Seel providing
   a fabricated Venmo transaction ID for a refund that did not in
   fact occur, and BBB / Trustpilot complaint patterns including
   indefinite "under review" status, biometric face-scan demands as
   a precondition for claim adjudication, and a documented chargeback
   collision against Seel directly.
3. Creality's request for direct ACH, wire, or SWIFT transfer
   information outside the original card-network payment rail, and
   the cardholder's declination of that request on standard
   card-network-refund-handling grounds.
4. The cardholder's assessment that the combination of (1) and (3)
   during an active chargeback period is, in cardholder's experience,
   consistent with coordinated chargeback-defeat conduct rather than
   genuine remediation.
5. Reaffirmation of the original 2026-06-17 sworn statements and
   continued support for the chargeback dispute.

The first supplemental is structured to be attached to the original
in the bank's dispute file. It does not replace or modify the original.

## 2026-06-24 Affirm investigator briefing

A separate briefing was provided to Affirm's investigator documenting
the BNPL-lender prejudice pattern that the Creality+Seel+ACH/wire
chargeback-defeat conduct creates for any BNPL lender financing a
purchase routed through this merchant-side pattern. The briefing
includes:

1. Substantive credentials and underlying-transaction context
2. The post-chargeback merchant conduct prejudicial to Affirm
   specifically
3. Documented public-record evidence about Seel including the active
   *Mickey v. Seel, Inc.* class action (N.D. Cal. case 4:26-cv-01336)
4. The bidirectional fraud-vector finding (Seel as both a merchant-
   side chargeback-defeat tool and a consumer-side BNPL-default fraud
   enabler)
5. Specific considerations for Affirm's investigator independent of
   the individual dispute resolution

## License

The case content (sworn statements, factual record, attestations) is
the personal record of the cardholder and is not licensed for
republication as if from another party. The methodology, forensic
analysis pattern, and template structure may be referenced and adapted
by other consumers for their own disputes under a permissive use
arrangement. Cite Obsidian Watch Group if helpful, but the goal here
is that the template is usable.

## Contact

For questions about adapting this pattern to your own dispute:
investigations@obsidianwatch.org

For coordinated reporting on Creality consumer-protection issues:
investigations@obsidianwatch.org

PGP: 9267 A71E 3F0A 4EED 2F97 3F9B A3E2 52F2 4635 CC6C
