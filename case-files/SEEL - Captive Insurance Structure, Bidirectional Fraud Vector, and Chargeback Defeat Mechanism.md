# Seel - Captive Insurance Structure, Bidirectional Fraud Vector, and Chargeback Defeat Mechanism

Status: Active OWG investigation. Anchored on the active class action *Mickey
v. Seel, Inc.* (N.D. Cal. case 4:26-cv-01336) which alleges Seel operates as
an unadmitted insurer in California through a wholly-owned captive insurance
subsidiary that does not in fact insure consumers. The OWG investigation
expands the litigation framing to document the structural mechanism by which
the Seel architecture enables both merchant-side chargeback-defeat conduct
and consumer-side BNPL-default fraud, with consumer-protection implications
beyond the California-specific licensing question.

Companion to: [[Creality Bank Dispute case file]] (the originating case),
[[Documented BNPL fraud patterns]] (planned), [[Captive insurance regulatory
gap documentation]] (planned).

## Posture

Seel, Inc. operates a Shopify and BigCommerce e-commerce "post-purchase
protection" platform that is marketed to merchants as a way to offer their
customers shipping insurance, return assurance, and product protection. The
public-facing claim is that consumers buy peace of mind; the structural
reality the case file documents is that the program operates as a captive
self-insurance arrangement with no actual consumer insurance protection, no
state regulatory oversight in California, and a set of operational
characteristics that make the program usable both as a merchant tool for
defeating active chargebacks and as a consumer tool for committing BNPL
(buy-now-pay-later) loan-default fraud.

The case file documents the structural pattern, not Seel's intent. The case
file does not assert that Seel designed the program specifically to enable
either fraud vector; it documents that the program's operational
characteristics in fact enable both, and that the documented complaint
pattern and the active class-action litigation indicate the structure is
not functioning as legitimate consumer insurance regardless of intent.

## Corporate structure

### Identity

- **Legal name**: Seel, Inc.
- **Original name**: Kover, Inc. (also referenced as "Kover AI"; rebranded
  to Seel circa 2020-2021)
- **Headquarters**: San Francisco, California
- **Insurance subsidiary**: Seel Insurance, Inc. (wholly-owned captive sub)
- **Founded**: 2018-2019
- **Founders**: Zack Peng (CEO) and Bill Liu

### Funding and investors

Seel has raised approximately $23.6 million across funding rounds. The
Series A of $17 million in January 2022 was led by Lightspeed Venture
Partners. Documented investors include:

- Lightspeed Venture Partners (Series A lead)
- Foundation Capital
- Afore Capital
- West Loop Ventures
- Fox Ventures
- Wischoff Ventures
- Jefferies

The investor list is conventional Silicon Valley early-stage venture capital
with no FASCSA-flagged backers visible in public records. The investment
posture is consistent with a SaaS / consumer-protection-tech narrative.

### Captive insurance subsidiary structure

The structural finding documented in the *Mickey v. Seel* class action and
confirmed in Seel's own public-facing materials: Seel Insurance, Inc. is a
**wholly-owned captive insurance subsidiary** of Seel, Inc. The captive sub
does not provide insurance to consumers in the conventional sense. It
provides insurance to its parent (Seel) against Seel's own contractual
obligations to consumers under the Worry-Free Purchase program terms.

This is structurally distinct from how legitimate consumer insurance works.
In conventional consumer insurance:

- A licensed admitted insurer underwrites consumer policies
- The state insurance commissioner regulates the insurer's solvency, claim
  handling, and conduct
- The state insurance guaranty fund protects consumers if the insurer fails
- The consumer is the named insured under the policy

In Seel's captive structure:

- Seel Insurance, Inc. (the captive sub) underwrites Seel, Inc. (its parent)
  against the parent's contractual exposure
- The consumer is not the named insured; the consumer is a third-party
  beneficiary of the parent's contractual obligation
- No state insurance commissioner regulates the captive sub on the
  consumer's behalf
- No state guaranty fund applies
- The "claim" the consumer files is technically a contractual claim
  against Seel, Inc., not an insurance claim against an admitted insurer

The practical effect: a Seel "refund" is Seel writing the consumer a check
out of operating capital, with no insurance regulator able to compel payment,
no guaranty fund backing if Seel becomes insolvent, and no statutory
bad-faith claim-handling penalties that would apply to a licensed insurer.

## *Mickey v. Seel, Inc.* class action

**Case**: *Mickey v. Seel, Inc.*
**Court**: United States District Court for the Northern District of California
**Case number**: 4:26-cv-01336
**Filed**: 2026 (reporting surfaced March 30, 2026)
**Class definition**: All consumers in the United States who purchased
Seel's "Worry-Free Delivery" or other shipping insurance products during the
applicable limitations period.

### Central allegations

1. Seel offers what it markets as "shipping insurance" to consumers.
2. Seel is not an admitted insurer in California.
3. California Insurance Code requires that entities offering insurance to
   California consumers be admitted insurers in the state.
4. The Seel Insurance, Inc. subsidiary is a captive insurer that insures
   only its parent, not consumers.
5. Consumers who purchased Seel's shipping insurance products did not
   receive what they paid for: legitimate, regulated consumer insurance.
6. Consumers who file claims and are denied have no statutory insurance-
   regulatory remedy because Seel is not a licensed insurer in California.

### Why this matters structurally

The class action is the legal vehicle for what the OWG investigation
documents at the structural level: the Seel program is not consumer
insurance. It is a contractual promise from a Silicon Valley venture-funded
startup that is structured to look like insurance for the purpose of
collecting premiums and that is structured to NOT look like insurance for
the purpose of evading insurance-regulator oversight.

## The bidirectional fraud vector

The OWG investigation documents two distinct fraud vectors enabled by the
Seel architecture. Both have been observed in the public-record complaint
pattern. The investigation's structural finding is that the Seel program's
operational characteristics make it usable as a fraud tool from both sides
of the merchant-consumer relationship, regardless of Seel's intent.

### Vector 1: Merchant-side chargeback defeat

Pattern: when a consumer initiates a card-network chargeback against a
merchant for a disputed transaction, the merchant redirects the consumer to
Seel as a "remediation pathway" during the active chargeback window.

Operational characteristics that enable this:

- Seel can issue refund-confirmation messages to the consumer (including
  fabricated transaction IDs as documented in the Sitejabber Venmo case;
  see below) that the merchant can use to tell the issuing bank
  "remediation has been offered and processed."
- Seel can request that the refund be deposited via direct ACH, wire, or
  SWIFT transfer, bypassing the original card-network payment rail. A
  refund processed outside the card network does not reverse the original
  card-network transaction and therefore does not prejudice the merchant's
  chargeback defense.
- Seel can indefinitely delay claim adjudication ("under review" status),
  preventing the consumer from definitively determining whether a refund
  is or is not coming, while the chargeback window with the bank progresses.
- Seel can deny the claim on manufactured grounds after the chargeback
  window has expired, leaving the consumer without recourse through either
  channel.

The merchant's incentive to use Seel as a chargeback-defeat tool: each
successful diversion preserves the merchant's chargeback ratio (which
affects merchant-account standing with the payment processor) and preserves
the merchant's revenue from the disputed transaction.

The consumer's exposure: the consumer can be diverted from the operative
remediation pathway (the bank chargeback) into a pathway with no
insurance-regulatory oversight, no card-network protection, and a
documented pattern of denials.

### Vector 2: Consumer-side BNPL-default fraud

Pattern: a bad-actor consumer purchases an expensive product through a
buy-now-pay-later (BNPL) lender (Affirm, Klarna, Afterpay, AfterPay, Sezzle,
or similar) at a merchant that offers Seel "Worry-Free Purchase" coverage,
purchases the Seel coverage at checkout, files a false porch-piracy or
non-delivery claim with Seel, receives a refund from Seel via direct ACH or
wire transfer to the bad actor's bank account (not back to the BNPL lender),
and then defaults on the BNPL loan.

Operational characteristics that enable this:

- Seel pays refunds via direct deposit to the consumer's bank account
  rather than back to the original BNPL or card-network funding source.
- The BNPL lender's loan is fully disbursed to the merchant at the point
  of purchase; the lender's recovery depends on the consumer making loan
  payments. If the consumer receives the underlying product AND receives
  a Seel refund AND defaults on the BNPL loan, the BNPL lender absorbs
  the full loss while the consumer keeps the product and the cash refund.
- Seel's claim adjudication does not require police reports in all cases
  (the documentation requirement is described as variable in Seel's public
  terms), making false-claim filing operationally tractable.
- The advertised "99% claim approval rate" creates a public-facing
  expectation that claims will be paid, encouraging the fraud strategy.

The bad-actor consumer's incentive: receive a product, receive cash equal
to the product's price, default on a loan that the BNPL lender pursues
through ordinary collection channels that may or may not be successful.

The BNPL lender's exposure: the lender absorbs both the underlying product
cost and the defaulted-loan loss. The lender has no direct relationship
with Seel and no recovery pathway against Seel's refund decisions.

The honest broker (legitimate consumer with a legitimate claim) exposure:
the fraud volume against the program incentivizes Seel to deny legitimate
claims as a defensive posture, hurting honest consumers and creating the
documented BBB / Sitejabber / Trustpilot complaint patterns.

### Why both vectors exist in the same program

The same operational characteristics that enable vector 1 (refund processed
outside card-network rails; direct ACH/wire deposit; flexible claim handling)
enable vector 2. Seel is operationally a money-mover that pays cash to
consumers who file claims, with the source of the cash being Seel's
operating capital (since Seel Insurance, Inc. is a captive sub).

A legitimate consumer insurer with state regulation would have specific
constraints that prevent both vectors:

- Refunds processed through the original payment rail (so BNPL lenders are
  whole and so merchant chargebacks operate normally)
- Mandatory state-defined documentation requirements (so false claims
  cannot be filed without verifiable proof)
- Regulator oversight of claim-handling timeliness (so chargeback windows
  don't expire while claims are "under review")
- Statutory bad-faith penalties for delayed or denied legitimate claims
- Guaranty fund backing for consumer recovery if the insurer fails

Seel's structure has none of these. The absence of state regulation is
what makes the program a bidirectional fraud vector.

## Documented complaint patterns

Public-record complaint sources consistently show patterns concentrated in
the operational categories that the structural analysis above predicts.

### The Sitejabber Venmo fake-transaction case

The most concretely documented case of refund-faking behavior is a
publicly-posted consumer review on Sitejabber documenting the following
sequence:

1. The consumer's Seel claim was "approved."
2. Seel notified the consumer that the refund had been processed via Venmo.
3. Seel provided the consumer with a Venmo transaction ID.
4. The consumer contacted Venmo to verify the transaction.
5. Venmo confirmed the transaction ID was NOT associated with any actual
   Venmo transaction. The transaction ID was fabricated.
6. The consumer presented this to Seel.
7. Seel revised its position to say the transfer "had not gone through."

The Sitejabber-documented sequence is operationally consistent with the
following: the fabricated transaction ID was provided to the consumer in
order to induce the consumer to withdraw a pending bank chargeback or to
accept the refund as completed and stop pursuing the matter. The subsequent
"the transfer hadn't gone through" revision is the standard fallback when
the fabrication is detected.

This case is a single Sitejabber post. The case file flags it as
single-source. The structural framework predicts that more cases would exist
because the documented operational characteristics make this kind of
behavior tractable as a chargeback-defeat tool. Substantiation pathway:
collect additional consumer reports of fabricated transaction IDs from
Seel; check whether any have been filed with California Department of
Insurance, FTC, or CFPB.

### BBB complaint pattern

Better Business Bureau records for Seel, Inc. (San Francisco location)
document complaints including:

- Returns received by Seel but no refund issued
- Claims indefinitely in "under review" status
- Claim denials for "shipping damage" vs "handling damage" recategorizations
- Communication cessation after denials
- Refunds promised but not delivered

### Sitejabber, Trustpilot, Shopify App Store

Reviews across these platforms document the same operational patterns plus
specific additional concerns:

- Biometric face-scan requirements as a precondition for claim adjudication;
  refusal of the biometric requirement resulting in claim closure
- Manufactured grounds for denial
- The advertised 99% approval rate inconsistent with the volume of complaints

### Documented chargeback collision

At least one publicly-documented consumer chargeback has been filed against
Seel itself, in addition to the underlying merchant. This pattern indicates
that Seel has been operationally treated by consumers as a separate adverse
party (not as a remediation pathway) by at least some claimants.

## The Creality case as anchoring example

The OWG Creality K2 Plus dispute case file (see companion repository
ObsidianGroup_CrealityDispute, affidavits dated 2026-06-17 and 2026-06-23)
documents the following sequence relevant to this case file:

1. Consumer initiated bank chargeback against Creality on 2026-06-17 for an
   undelivered $700 product (Creality CR-Scan Otter 3D scanner) for which
   only routine printer consumables were received.
2. On 2026-06-22, during the active chargeback period, Creality notified
   the consumer in writing that Creality had "contacted Seel Insurance to
   extend your case" and instructed the consumer to file a Seel claim.
3. In subsequent correspondence regarding refund processing, Creality
   requested that the consumer provide direct ACH, wire, or SWIFT
   transfer information for the deposit of a refund outside the
   card-network payment rail.
4. The consumer declined to provide direct banking transfer information.
5. The consumer maintained the chargeback dispute and submitted a
   supplemental affidavit (2026-06-23) documenting the Seel redirection
   and the ACH/wire request as additional dispute evidence.
6. The consumer also notified Affirm (the BNPL lender that financed the
   original purchase) that the redirection of the refund outside the
   original payment rail prejudices Affirm's loan recovery and that
   refunds must be returned to Affirm per the original loan agreement.

The Creality case is operationally typical of the merchant-side
chargeback-defeat vector. The combination of (a) Seel redirection during an
active chargeback, (b) the ACH/wire request to bypass card-network rails,
and (c) the timing during the dispute window is the operational signature
of the vector documented above.

The Creality case is also operationally distinctive in that the consumer
identified the pattern in real time and took the additional protective step
of notifying the BNPL lender (Affirm) that the merchant's proposed refund
pathway prejudices the lender's loan recovery. This is an unusual
defensive move because most consumers in the merchant-side vector are not
positioned to articulate why direct-ACH refund deposits cut the BNPL lender
out of the recovery chain. The Creality case file documents this protective
move as a template for other consumers facing the same vector.

## Comparison to legitimate shipping insurance

Legitimate consumer shipping insurance products are typically:

- Underwritten by state-admitted insurers (e.g., Liberty Mutual, Chubb,
  Travelers) or by carrier-affiliated specialty programs (UPS Capital,
  FedEx insurance) that are regulated through carrier-level requirements
- Subject to state insurance commissioner oversight of claim handling
- Required to process refunds in defined timeframes
- Backed by state guaranty funds for consumer recovery if the insurer fails
- Required to publish loss-ratio data and claim-handling metrics

Specific examples of legitimate consumer-protection programs that operate
differently from Seel:

- UPS Capital Insurance Agency, Inc.: licensed insurance agent, places
  policies with admitted insurers, subject to state insurance regulation
- USPS Insurance: federal program with statutory claim-handling rules
- FedEx Declared Value: contractual carrier liability under common-carrier
  framework with carrier-level regulation
- Major retailer warranty programs (e.g., Best Buy Geek Squad Protection):
  underwritten by admitted insurers (typically AIG WarrantyGuard or similar
  for major retailers), subject to state insurance regulation

Seel's captive-insurance structure has no equivalent in the legitimate
consumer-protection-insurance market. The model is more analogous to
unregulated extended-warranty programs that have themselves been the
subject of state and federal enforcement actions over the past 15 years.

## Structural finding

The Seel architecture documents a category of financial-intermediary fraud
vector that the existing consumer-protection regulatory framework was not
designed to address. The pattern:

1. Silicon Valley venture-funded startup positions itself as a consumer
   protection program.
2. The program's underwriting entity is a wholly-owned captive subsidiary
   that does not actually insure consumers.
3. The program is marketed through e-commerce platforms (Shopify,
   BigCommerce, Adobe Commerce) to small and mid-size merchants at scale.
4. The program's operational characteristics (off-rail refund deposits,
   flexible documentation requirements, indefinite claim review, no state
   regulator oversight) make it usable as both a merchant-side
   chargeback-defeat tool and a consumer-side BNPL-default fraud tool.
5. The documented complaint pattern across BBB, Sitejabber, Trustpilot,
   Shopify App Store, and the active *Mickey v. Seel* class action
   confirms that the operational characteristics are in fact being used
   in ways inconsistent with legitimate consumer insurance.

The pattern has implications beyond Seel specifically. The
captive-insurance-startup-as-consumer-protection-marketing pattern is
adopted by additional companies in the e-commerce-protection space (Route,
Loop, Corso, others) with varying degrees of admitted-insurer underwriting.
The structural framework documented here is a tool for evaluating those
programs as well.

## Investigation priorities

1. **Confirm Seel Insurance, Inc.'s captive structure** through state
   incorporation filings and California Department of Insurance records.
   The *Mickey v. Seel* complaint relies on California Insurance Code
   admissions data; the same data is publicly available.

2. **Map Seel's merchant customer base** for PRC-domiciled merchant
   concentration. The Creality anchor case is a PRC-headquartered
   merchant. Documenting whether Seel disproportionately serves
   PRC-headquartered merchants would be a substantive finding about the
   program's structural alignment with cross-border merchant interests
   that may not have legitimate U.S. consumer remediation reach.

3. **Quantify the BBB / Sitejabber / Trustpilot / Shopify complaint volume**
   for time-series patterns and category analysis. The volume relative to
   the merchant-customer count is meaningful; the category distribution
   relative to legitimate-insurance industry benchmarks is meaningful.

4. **Track the *Mickey v. Seel* class action** for procedural developments,
   document production, and any settlement structure. Class action
   discovery may produce evidence about the captive-insurance structure
   that is not available through public-record research.

5. **Document additional fabricated-transaction-ID cases** if any can be
   surfaced. The Sitejabber Venmo case is single-source; a documented
   pattern of fabricated transaction IDs would substantively strengthen
   the merchant-side chargeback-defeat vector documentation.

6. **Engage California Department of Insurance, FTC, and CFPB** with
   complaint filings documenting the structural pattern. The complaint
   filings themselves become public-record evidence of the pattern's
   recognition by regulators.

7. **Investigate analogous programs** (Route, Loop, Corso, others) for
   the same captive-insurance-startup pattern. Documenting that the
   pattern is industry-wide rather than Seel-specific changes the
   regulatory and litigation framing.

8. **BNPL lender coordination**: Affirm, Klarna, Afterpay, Sezzle, and
   similar lenders are the financial parties most directly exposed to the
   consumer-side BNPL-default fraud vector. Coordinated lender awareness
   of the vector and lender-side anti-fraud measures could close the
   vector at the financial-flow level.

## Sources

### Class action
- *Mickey v. Seel, Inc.*, N.D. Cal. case 4:26-cv-01336 complaint:
  classaction.org/media/mickey-v-seel-inc-complaint.pdf
- ClassAction.org news coverage:
  classaction.org/news (search "Seel")

### Corporate and funding
- Seel Crunchbase profile (original "Kover AI" slug):
  crunchbase.com/organization/kover-ai
- Seel PitchBook profile:
  pitchbook.com/profiles/company/279650-98
- Lightspeed Venture Partners portfolio:
  lsvp.com/company/seel/
- TechCrunch Series A reporting (January 2022):
  techcrunch.com/2022/01/13/seel-secures-17m-round-to-infuse-ai-in-customer-product-returns/

### Founder
- Zack Peng Crunchbase: crunchbase.com/person/zack-peng
- Zack Peng LinkedIn: linkedin.com/in/zackpeng/

### Consumer complaints
- BBB Seel, Inc., San Francisco profile:
  bbb.org/us/ca/san-francisco/profile/information-technology-services/seel-inc-1116-962928
- Sitejabber Seel reviews (includes Venmo fake-transaction case):
  sitejabber.com/reviews/seel.com
- Trustpilot Seel reviews:
  trustpilot.com/review/seel.com
- Shopify App Store Seel Worry-Free Purchase reviews:
  apps.shopify.com/return-assurance/reviews

### Program documentation
- Seel main site: seel.com
- Seel terms of service: seel.com/faq/learn-more-about-seel-worry-free-purchase
- Seel merchant docs: developer.seel.com/docs/using-the-merchant-dashboard
- Seel support (legacy Kover branding visible): kover2618.zendesk.com/hc/en-us

## Methodology and standard of evidence

This case file applies the OWG investigation methodology:

- Documented facts are sourced to verifiable primary documentation
- Analytical inference is flagged as inference
- Single-source claims are explicitly noted as single-source (the
  Sitejabber Venmo fake-transaction case is flagged single-source pending
  additional documented cases)
- No allegation of criminal conduct against specific living individuals
  absent court records or charging-authority documentation
- The case file does not assert that Seel, its founders, or its investors
  designed the program with intent to enable the documented fraud vectors.
  It documents that the program's operational characteristics in fact
  enable both vectors, and that the documented complaint pattern and
  active litigation indicate the structure is not functioning as
  legitimate consumer insurance regardless of intent.

The structural-finding framing is the strongest claim the case file makes.
The structural finding does not depend on proof of intent; it depends on
the documented operational characteristics, the documented complaint
pattern, and the *Mickey v. Seel* litigation framing of the captive-
insurance structure.

---

*Last updated: 2026-06-23 (initial creation)*
*Investigator: Reckoner / Jay Puckett, Obsidian Watch Group*
*Anchored on: Mickey v. Seel class action structural framing, Creality K2
Plus dispute as merchant-side vector example, Sitejabber Venmo
fake-transaction case as documented refund-faking behavior, the
bidirectional fraud-vector observation as the structural-finding spine.*
