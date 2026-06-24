# Affirm Chat Message - Full-Order Refund Demand

**Date drafted**: 2026-06-24
**For**: Affirm chat / dispute escalation
**Submitter**: Jay Puckett

This is a chat-format message. Adapt as needed for the Affirm chat
interface. Reference documentation: the OWG case file at
github.com/jpuckett11/CrealityK2Plus_sweep with sworn affidavits,
firmware extraction findings, and network-forensic evidence.

---

## Suggested chat message

I'm escalating my Creality dispute. My original bank chargeback was for the SpeedX-shipped package that didn't arrive (the Otter scanner, bed, and nozzles). After investigating the Creality K2 Plus I received, I am now requesting refund of the ENTIRE Affirm loan covering this order - the K2 Plus printer + the CFS module + the Otter bundle. The basis has changed.

The Creality K2 Plus is not the product I purchased. It was advertised as a 3D printer with optional cloud features. What I received is documented to operate as a surveillance platform with 3D printing as the user-facing feature. The findings are in my published case file at github.com/jpuckett11/CrealityK2Plus_sweep. Specifically:

- The device captures camera frames continuously at 1920x1080@15fps regardless of whether anyone is viewing or printing
- The device uploads /var/log/* (the entire Linux system log directory) to Creality cloud by default, default-enabled
- The device maintains persistent cleartext connection to PRC-jurisdiction infrastructure (Alibaba Cloud MQTT) regardless of user cloud-feature engagement
- The device contains a remote command execution architecture (`dev_agent` Go binary) that decrypts AES-CBC encrypted commands from the cloud and executes them as root
- The consent UI is non-functional: declining consent at first-boot does not change the on-disk data collection flags
- The device transmits across at least seven distinct cloud infrastructure providers (Cloudflare, Alibaba, AWS US-East-1 with 3 endpoints, Macarne, GitHub Pages, Northeastern University NTP)
- I have observed the device transmitting roughly three times the bandwidth of my personal desktop computer during routine operation

Applicable legal framework:

**Fair Credit Billing Act, 15 U.S.C. § 1666i** (claims-and-defenses): a cardholder using credit to purchase goods can assert against the creditor any claim or defense the cardholder has against the merchant, when the purchase exceeds $50 and is within the cardholder's state or within 100 miles. BNPL lenders including Affirm follow analogous consumer-protection principles. I am asserting the merchant's misrepresentation claim against Affirm in this capacity.

**Truth in Lending Act / Regulation Z § 1026.12(c)**: the federal "claims and defenses" rule for credit transactions provides the same standing.

**Magnuson-Moss Warranty Act, 15 U.S.C. §§ 2301-2312**: implied warranty of merchantability and fitness for particular purpose. The product as documented does not satisfy the merchantable definition of "3D printer." Goods that surveille the consumer without specific disclosure cannot be merchantable to the consumer market without that disclosure.

**Tennessee Consumer Protection Act, T.C.A. § 47-18-104(a)(5) and (7)**: prohibits representing that goods have characteristics they do not have, and representing that goods are of a particular standard, quality, or grade when they are of another. The Creality K2 Plus was sold as a "3D printer with optional cloud features." It was delivered as a surveillance platform with mandatory cloud-side telemetry, default-enabled system log exfiltration, persistent PRC-jurisdiction connections, and remote command execution architecture - none of which were disclosed in the consumer-facing product description.

**FTC Act, Section 5**: federal prohibition on unfair or deceptive practices. A parallel FTC complaint is being filed in this case.

I am asking Affirm to:

1. Refund the entire purchase amount to my Affirm balance and zero out the loan
2. Pursue Creality through Affirm's merchant-account dispute process for the merchandise-not-as-described claim
3. Note this case in your records as merchandise-not-as-described and as a documented surveillance-architecture finding, not as a simple non-delivery case

Documentation:

- Public case file: github.com/jpuckett11/CrealityK2Plus_sweep
- Sworn affidavits (PGP-signed, attached to my bank dispute): 2026-06-17 original, 2026-06-23 first supplemental documenting Creality's chargeback-defeat conduct, 2026-06-24 second supplemental documenting the SpeedX delivery account
- Parallel regulatory filings: FTC, CISA, California Attorney General, Tennessee Attorney General, California Department of Insurance (regarding Seel), Consumer Financial Protection Bureau, Mozilla "Privacy Not Included"
- The 2026-06-24 Affirm investigator briefing previously sent to your investigator documenting the BNPL-lender prejudice pattern

I am available for follow-up questions. My contact: investigations@obsidianwatch.org. PGP: 9267 A71E 3F0A 4EED 2F97 3F9B A3E2 52F2 4635 CC6C.

---

## Tactical notes

1. **The pivot from partial to full refund is legally clean.** Your original
   chargeback was for the SpeedX-undelivered portion only. The new findings
   change the basis: the part you DID receive (the K2 Plus printer and CFS
   module) was misrepresented at the product-character level. That's a
   different claim than non-delivery. You can pursue both simultaneously
   without contradiction.

2. **The FCBA claims-and-defenses provision is your strongest single
   legal lever for Affirm**, because it specifically addresses the
   creditor-merchant-consumer triangle. Affirm cannot pursue you for the
   loan if the underlying merchant claim is valid and asserted.

3. **Magnuson-Moss is the parallel federal lever** - it doesn't require the
   FCBA-style purchase-amount or proximity thresholds. It applies to
   warranted consumer products and implies warranty of merchantability for
   all consumer goods.

4. **The Tennessee Consumer Protection Act** is your state-level lever.
   §47-18-104(a)(5) and (7) are the most directly relevant subsections
   for misrepresentation of product characteristics.

5. **Don't agree to a partial refund as a settlement** that closes the
   case. The structural findings have value beyond this individual
   transaction. Settle for full refund or pursue the regulatory and
   journalism filings to completion.

6. **Affirm's interest aligns with yours** here. They lose money if the
   merchant doesn't make them whole. Pushing this through Affirm's
   merchant-account dispute mechanism is in their interest as much as
   yours.

---

*Draft 2026-06-24. Edit before sending. Send via Affirm chat
interface or via Affirm's formal dispute channel as appropriate.*
