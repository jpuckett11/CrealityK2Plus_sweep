# Briefing for Affirm Investigator

**Submitting party**: Jay Puckett (Reckoner)
**Lead Investigator, Obsidian Watch Group**
**Email**: investigations@obsidianwatch.org
**PGP fingerprint**: 9267 A71E 3F0A 4EED 2F97 3F9B A3E2 52F2 4635 CC6C
**Date**: 2026-06-24
**Subject**: Coordinated chargeback-defeat and BNPL-lender prejudice
pattern involving Creality (Shenzhen Creality 3D Technology Co., Ltd.)
and Seel, Inc.

---

## 1. Purpose of this briefing

I am the Affirm borrower of record for the financed purchase of a
Creality CR-Scan Otter 3D scanner that is the subject of an active bank
chargeback dispute. I am providing this briefing to Affirm's
investigator because the merchant's post-chargeback conduct prejudices
Affirm's loan recovery in a way that is operationally distinct from the
original misrepresentation, and because the conduct fits a documented
structural pattern that Affirm has direct standing to address with the
merchant independent of the underlying consumer dispute.

This briefing is provided in good faith and at my own initiative. I am
not requesting any modification of my loan terms, any extension, or any
forbearance. I am providing the briefing because the merchant's conduct
threatens Affirm's loan principal recovery, and Affirm's investigator
should have the documented record before any of the merchant's
subsequent moves are processed.

## 2. Submitting party credentials

I serve as Lead Investigator at Obsidian Watch Group, an independent
investigative organization with a public case file portfolio (see
github.com/jpuckett11/ObsidianGroup_RealCostOfIsrael and
github.com/jpuckett11/ObsidianGroup_Epstein). I have federal expert-
witness testimony experience including in matters involving consumer
hardware supply chain and connected-device security. My investigator
profile is verifiable through standard channels.

I mention this because the documentation pattern in this briefing
reflects investigative methodology rather than ad-hoc consumer
complaint, and Affirm's investigator should weigh the evidentiary
discipline accordingly.

## 3. Underlying transaction and original dispute

- **Merchant**: Creality (Shenzhen Creality 3D Technology Co., Ltd.),
  U.S. presence at City of Industry, California.
- **Product represented as shipped**: Creality CR-Scan Otter 3D scanner
  (retail approximately $700 USD).
- **Product actually received**: routine 3D printer consumables (a
  print bed and a small quantity of replacement heater-nozzle
  assemblies). No 3D scanner of any kind, no item of value comparable
  to the merchant's $700 representation.
- **Funding**: financed via Affirm at point of purchase.
- **Bank chargeback initiated**: 2026-06-17.
- **Bank chargeback affidavit (sworn under penalty of perjury)**:
  available as `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.pdf`
  and `Creality_Dispute_Affidavit_2026-06-17_SANITIZED.pdf.asc` (PGP-
  signed) in the companion `ObsidianGroup_CrealityDispute` repository.
  Supplemental affidavit (2026-06-23) documents the post-original
  conduct that is the subject of this briefing.

The original sworn affidavit documents the substitution conduct, the
three-package split shipment across two FedEx and one off-brand
courier, the merchant's tracking opacity on its own customer portal,
the absence of any network-traffic evidence of the CR-Scan Otter ever
being on the cardholder's home network (corroborative; the device is
WiFi-enabled and announces via mDNS upon first power-on), and the
public-record context of 67 unanswered BBB complaints against the
merchant in the most recent three-year period.

The underlying dispute is operationally complete. The merchant has not
produced the carrier weight and dimension records, proof of delivery,
or warehouse pick list that would substantiate the merchant's
representation that a $700 scanner was actually shipped. The merchant's
non-engagement with the substantive dispute is the documented record.

## 4. The post-chargeback merchant conduct that prejudices Affirm

On 2026-06-22, during the active period of the bank chargeback
dispute, the merchant communicated to me in writing:

> "Hello, we have contacted Seel Insurance to extend your case. Please
> submit your claim as soon as possible. If you have any further
> questions, please contact us. Thank you for your understanding!"

In subsequent communications regarding refund processing, the merchant
requested that I provide direct ACH, wire, or SWIFT transfer
information for the deposit of a refund. The request was for routing
and account information sufficient to initiate a direct bank deposit
of refund funds, **outside the original Affirm-funded card-network
payment channel**.

I declined this request in writing and notified the merchant that
refunds for the Affirm-funded purchase must be processed back to the
original payment method per the Affirm purchase agreement and per
standard card-network refund-handling practice. The merchant has not,
to date, processed any refund through the original payment channel,
nor produced the substantive dispute records the bank chargeback
process can compel.

## 5. Why this specifically prejudices Affirm

If the merchant succeeds in routing a refund via direct ACH, wire, or
SWIFT deposit to a borrower's bank account (or, in a fraud variant
described below, to a third party), the operational consequences are:

1. **Affirm does not receive returned loan principal.** The refund
   bypasses the Affirm-merchant payment rail. Affirm's loan principal,
   which was disbursed to the merchant at the point of purchase,
   remains in the merchant's possession.

2. **The cardholder's bank chargeback may be defeated.** The merchant
   can represent to the bank that a refund has been processed (and
   may, per the documented Seel conduct described in §6 below, even
   provide a fabricated transaction ID as evidence). The bank may
   reverse the chargeback on the basis of the apparent refund.

3. **Affirm is left with no recovery pathway.** With the chargeback
   reversed and the refund routed outside the Affirm channel, Affirm's
   only remaining recovery against the consumer loan is the borrower's
   continued repayment. If the borrower defaults, Affirm absorbs the
   full loss with no merchant-side recovery option.

In the present case, I am not a defaulting borrower and I have
declined the merchant's off-rail refund offer specifically because I
recognize this prejudice. **However, in cases where the borrower is a
bad actor (the "consumer-side BNPL-default fraud" vector described
below), Affirm is the party most exposed to the structural loss.**

## 6. The Seel intermediary and the structural fraud pattern

Seel, Inc. (the entity the merchant has named in the redirection
communication) is a Silicon-Valley-venture-funded e-commerce post-
purchase-protection platform. Affirm's investigator should be aware of
the following documented public-record items about Seel:

### 6.1 Active class action: Mickey v. Seel, Inc.

- **Case**: *Mickey v. Seel, Inc.*
- **Court**: U.S. District Court for the Northern District of
  California
- **Case number**: 4:26-cv-01336

The class action alleges that Seel offers shipping insurance as an
**unadmitted insurer** in violation of California Insurance Code, and
that Seel Insurance, Inc. is a wholly-owned captive insurance
subsidiary that does not actually insure consumers but rather insures
its parent Seel against contractual exposure to consumers. The class
definition encompasses all U.S. consumers who purchased Seel's "Worry-
Free Delivery" or other shipping insurance products during the
applicable limitations period.

Source: classaction.org/media/mickey-v-seel-inc-complaint.pdf

### 6.2 Documented fake-refund-transaction-ID conduct

A publicly-posted consumer review on Sitejabber (reviews of seel.com)
documents the following sequence: Seel notified a consumer that a
refund was processed via Venmo and provided a Venmo transaction ID.
The consumer contacted Venmo to verify. Venmo confirmed the
transaction ID was not associated with any actual Venmo transaction.
The consumer presented this to Seel. Seel then revised its position to
state that the transfer "had not gone through."

This documented case is consistent with the operational pattern of
providing fabricated transaction confirmations to consumers in order
to induce withdrawal of pending chargebacks. Sources:
sitejabber.com/reviews/seel.com.

### 6.3 BBB documented complaint pattern

Better Business Bureau records for Seel, Inc. (San Francisco location)
document complaints including refunds not issued despite Seel
receiving returned merchandise, claims indefinitely in "under review"
status, biometric face-scan demands as preconditions for claim
adjudication, manufactured grounds for denial, and communication
cessation following denials.

Source: bbb.org/us/ca/san-francisco/profile/information-technology-
services/seel-inc-1116-962928

### 6.4 The bidirectional fraud-vector finding

The Obsidian Watch Group structural investigation of Seel (case file
under the title "SEEL - Captive Insurance Structure, Bidirectional
Fraud Vector, and Chargeback Defeat Mechanism") documents that the
same operational characteristics that enable merchant-side chargeback
defeat enable a consumer-side BNPL-default fraud vector:

**Vector**: A bad-actor consumer purchases an expensive product
through a BNPL lender (Affirm, Klarna, Afterpay, Sezzle) at a merchant
that offers Seel "Worry-Free Purchase" coverage, purchases the Seel
coverage at checkout, files a false porch-piracy or non-delivery claim
with Seel, receives a Seel refund via direct ACH or wire transfer to
the bad actor's bank account (NOT back to the BNPL lender), and
defaults on the BNPL loan. The bad actor keeps the product and the
cash; the BNPL lender absorbs both the original loan principal loss
and the underlying product cost.

This vector is enabled by the same off-rail refund-deposit pathway
the merchant in my case is currently requesting. Whether or not the
present case is itself fraudulent, the structural pattern is
documented. **Affirm is the party most directly exposed to this fraud
vector across the broader merchant base that uses Seel as a "remediation
intermediary."**

The OWG investigation case file is available on request and will be
made publicly available through the standard OWG repository channels.

## 7. The merchant's broader operational disposition

In addition to the dispute-handling conduct described above, the OWG
investigation into Creality documents the merchant's operational
disposition across three layers (technical, commercial, regulatory).
The umbrella case file "CREALITY - Coordinated Extraction Disposition
Across Three Operational Layers" describes:

- **Technical layer**: documented network-forensic behavior including
  hardcoded PRC-jurisdiction NTP source bypassing DNS controls,
  persistent consent-flag values regardless of user refusal, persistent
  account-identity binding without user account creation, cleartext
  MQTT telemetry to Alibaba Cloud infrastructure, Tencent Hunyuan LLM
  integration for camera-frame and 3D-model data. Documented in the
  OWG `CrealityK2Plus_sweep` repository (May 2026 investigation,
  firmware V1.1.5.5 OEM code `CR0CN240110C10`).

- **Commercial layer**: 67 unanswered BBB complaints in three years
  (the merchant is not BBB-accredited); the documented shipping-
  pattern asymmetry; the substitution conduct in my case; **account-
  identity-tagged SKU-category-specific purchase restriction on
  Creality's direct-store website** that the investigator has verified
  is applied specifically to my customer identity and specifically to
  the SKU category (Mainboard) containing the hardware required for
  comparative investigative work. This is engineered behavior, not
  default fraud-prevention behavior.

- **Regulatory layer**: the present dispute, the Seel redirection, the
  ACH/wire payment-rail bypass request, the timing of all of these
  during the active chargeback window.

The structural finding the OWG investigation documents is that the
merchant exhibits a coordinated operational disposition across all
three layers. The dispute-handling conduct affecting Affirm is not
isolated; it is consistent with the merchant's documented disposition
across other operational domains.

## 8. The merchant's account-identity-tagged blocking finding,
relevant to investigator credibility assessment

I note for Affirm's investigator that the merchant has implemented
account-identity-tagged SKU restriction on its direct-store website
targeting specifically my customer account. The restriction is
verified by differential testing (logged in to my customer account,
the Mainboard category is greyed out; in a Firefox Private Browsing
session routed through a VPN exit with no cookies, the same category
is fully accessible). The restriction is SKU-category-specific (other
categories remain accessible from my customer account).

This is documented because:

1. It establishes that the merchant recognizes me as an adversarial
   party with sufficient operational profile to engineer against. The
   merchant's disposition toward this dispute is not standard customer
   dispute disposition.
2. It corroborates that the merchant's communication to me regarding
   the Seel redirection and the ACH/wire request is not standard
   customer service routing; the merchant is treating my account
   differentially.
3. It supports the broader case file finding that the merchant's
   disposition is engineered, not default.

## 9. What I am asking Affirm to consider

I am not requesting that Affirm take any specific action in my dispute.
I am requesting that Affirm's investigator consider the following:

1. **Decline to release the loan from Affirm's recovery position if
   the merchant insists on routing a refund outside the Affirm payment
   rail.** Refunds for Affirm-funded purchases must return to Affirm
   per the standard merchant agreement and per the Affirm purchase
   agreement with the borrower. The merchant's preferred off-rail
   pathway is not consistent with that requirement.

2. **Support the bank chargeback through any standard
   coordination Affirm extends to issuing banks.** A successful
   chargeback recovers Affirm's loan principal through the original
   payment rail.

3. **Investigate the broader merchant-side use of Seel as a
   chargeback-defeat intermediary across the Affirm merchant base.**
   This is the case where Affirm's investigation can produce
   structural protection beyond my individual case. The bidirectional
   fraud-vector documented in §6.4 above is the structural risk that
   warrants Affirm's attention.

4. **Note the merchant's documented operational disposition for the
   merchant-account risk assessment.** Creality's documented public-
   record complaint pattern, BBB non-engagement, account-identity-
   tagged investigator blocking, and the active dispute conduct in my
   case warrant the merchant-account risk attention Affirm extends to
   any merchant exhibiting this pattern.

## 10. Documentation available

The following documents are available to Affirm's investigator under
appropriate confidentiality terms if helpful to your review:

- Original 2026-06-17 sworn chargeback affidavit (PGP-signed, sanitized
  for distribution)
- 2026-06-23 supplemental affidavit documenting the Seel redirection
  and ACH/wire request (PGP-signed)
- The OWG `CrealityK2Plus_sweep` final findings report (28KB,
  publicly available at the OWG repository)
- The OWG umbrella Creality investigation case file
- The OWG Seel investigation case file
- Screenshots of the account-identity-tagged blocking on the
  Creality direct-store website (differential testing evidence)
- The verbatim merchant communications referenced above (the
  "we have contacted Seel Insurance to extend your case" message;
  the ACH/wire/SWIFT request)
- Public-record reference points for the Mickey v. Seel class action,
  the Sitejabber Venmo-fake-transaction case, and the BBB complaint
  patterns for both Creality and Seel

## 11. Contact

investigations@obsidianwatch.org

PGP fingerprint: 9267 A71E 3F0A 4EED 2F97 3F9B A3E2 52F2 4635 CC6C

Available on `keys.openpgp.org` and `keyserver.ubuntu.com`.

I am available for follow-up correspondence by email or by scheduled
call as Affirm's investigation process requires.

---

**Drafted 2026-06-24 in support of Affirm's investigator review.**

*The text of this briefing is unsigned at the briefing-document level.
Statements of fact about the underlying transaction and the present
dispute are also documented in the PGP-signed sworn affidavits
referenced above. PGP-signed version of this briefing available on
request.*
