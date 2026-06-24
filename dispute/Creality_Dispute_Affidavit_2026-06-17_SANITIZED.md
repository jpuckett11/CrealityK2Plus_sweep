> **SANITIZED FOR PUBLIC DISTRIBUTION.** This version replaces the
> specific network-device identifier of the cardholder's 3D printer
> (the K2 Plus's unique model-suffix and mDNS service identifier) with
> placeholders to prevent fingerprinting of the residential network.
> The original signed and unsanitized version remains in the
> cardholder's private records and the bank's dispute file. The case
> facts, sworn statements, and analysis are otherwise unchanged.

---

# Affidavit and Sworn Statement in Support of Disputed Transaction

**Cardholder:** Jay Puckett
**Email:** investigations@obsidianwatch.org
**Date of affidavit:** 2026-06-17
**Merchant:** Creality (Shenzhen Creality 3D Technology Co., Ltd.)

---

## 1. Purpose of this statement

I, Jay Puckett, am the cardholder of record for the transaction currently in dispute with Creality. I am submitting this statement under penalty of perjury, in support of the chargeback already initiated with my bank.

The merchant has represented to my bank that they shipped me a Creality CR-Scan Otter 3D scanner (a product retailing for approximately $700 USD). **They did not.** I am submitting this affidavit to attest to that fact, to add my profile and supporting context to the case file, and to provide network-traffic evidence corroborating that the represented merchandise was never delivered to my possession.

## 2. What was actually received

The package I received from Creality contained:

- One (1) 3D printer build plate / print bed (replacement consumable)
- A small number of replacement heater-nozzle assemblies (consumable parts)

The package did NOT contain:

- A Creality CR-Scan Otter 3D scanner
- Any 3D scanner of any kind
- Any item of value comparable to the merchant's $700 claim

The actual retail value of the items received is consistent with a routine consumables order for an existing 3D printer, not a $700 scanner shipment.

## 3. My existing 3D printing equipment and customer profile

I am an existing Creality customer. I own a **Creality K2 Plus** 3D printer (model identifier `K2Plus-XXXX`). The items I actually received (print bed and nozzles) are consumables compatible with my existing K2 Plus printer, consistent with a routine replacement-parts order.

For full context on the nozzle situation: I have been replacing the original heater-nozzle assemblies on my K2 Plus with **Micro Swiss aftermarket heater-nozzle assemblies** (a third-party brand) for improved hot-end performance. The Micro Swiss replacements are a hardware upgrade I performed myself; they are independent of any Creality shipment and unrelated to the disputed transaction.

I mention this only because the package I received from Creality contained nozzle parts that I have NOT installed and do NOT intend to install, given my move to Micro Swiss. The presence of those Creality nozzles in the package further confirms that the shipment was a routine-parts shipment, not the $700 scanner Creality claims.

## 4. Network-traffic evidence: the CR-Scan Otter has never been on my network

The Creality CR-Scan Otter is a WiFi-enabled 3D scanner. Per Creality's own product documentation, it advertises itself on the local network via mDNS (multicast DNS / Bonjour) under the `_Creality-*._udp` service type, matching the pattern Creality uses for all of their networkable products.

My existing Creality K2 Plus printer follows this same pattern and is observable on my home network as expected. A live capture of mDNS announcements on my home network at the time of this affidavit shows:

```
+ wlp11s0 IPv4 K2Plus-XXXX    _Creality-XXXXXXXXXXXX._udp local
+ wlp11s0 IPv6 K2Plus-XXXX    _Creality-XXXXXXXXXXXX._udp local
+ wlp11s0 IPv4 EPSON WF-2930  _scanner._tcp                  local
+ wlp11s0 IPv6 EPSON WF-2930  _scanner._tcp                  local
```

The K2 Plus 3D printer announces itself correctly. An Epson WF-2930 multifunction printer (which has scan-to-network capability) also announces itself correctly under the standard `_scanner._tcp` service type.

**No Creality CR-Scan Otter, no CR-Scan device, no Creality-branded 3D scanner of any kind has ever announced itself on my home network.** If the CR-Scan Otter had been delivered and ever powered on within range of my network (which is the necessary first-use step for the device per Creality's setup instructions), it would have generated an mDNS announcement and would be visible in the capture above. It is not.

This evidence is corroborative, not conclusive on its own. The absence of a network announcement is consistent with "the device was never delivered." It is also consistent with "the device was delivered but never powered on," which itself contradicts any merchant claim that I received and used the device.

A separate, longer mDNS capture sample is included as a supplementary exhibit to this affidavit. The supplementary capture is PGP-signed by the same key that signs this affidavit, so the bank can verify both documents are authentic and have not been modified after signing.

Additionally, my system logs show no record of:

- Any USB connection of a Creality CR-Scan Otter to any computer in my household
- Any Creality scanner software installation
- Any Creality CR-Scan-branded service registration on my network

The complete absence of any record of the device on my technical infrastructure is evidence that the device was never in my possession.

## 5. Shipping pattern observation - forensic indicators worth the bank's attention

The merchant fulfilled this order in a shipping pattern that is unusual for a single $700+ product and is worth the bank's investigative attention as part of the dispute:

1. **Three (3) separate packages** were used for what the merchant represents as a single order.
2. **Two (2) packages were shipped via FedEx**, which has standard proof-of-delivery and tracking processes.
3. **One (1) package was shipped via an off-brand courier**, not FedEx and not another major carrier, and with no recognizable carrier identity I could verify.
4. **The merchant's own website does not show accessible tracking detail for the order**. I have been unable to locate the tracking numbers or per-package shipment information through the merchant's customer-facing order portal.

Each of these would be a minor irregularity on its own. Together they form a pattern that is forensically inconsistent with a legitimate $700 product shipment:

- A $700 product is normally shipped insured, in a single package, via a major carrier with strong proof-of-delivery and customer-visible tracking.
- Splitting a high-value item across carriers dilutes single-package verification.
- Routing one package through an off-brand courier with weak delivery-verification removes the strongest evidentiary safeguard.
- Failing to surface tracking detail on the merchant's own site removes the customer's ability to independently verify shipment claims.

The combined effect of the merchant's shipping choices is that I, as the customer, have no independent way to confirm what was actually shipped, when, by whom, or to where. The merchant retains all evidentiary control over the shipment record.

This pattern is consistent with intentional fraud architecture, not order-processing error. I respectfully ask the bank to exercise its dispute-process powers to compel Creality to produce:

- All three tracking numbers and carrier names for each package
- Carrier-reported weight and dimension records for each package (a CR-Scan Otter retail box weighs approximately 1.5-2 kg; a 3D printer build plate weighs approximately 400-600g; replacement nozzles weigh under 100g - if the merchant cannot produce a carrier weight record consistent with a 1.5+ kg package containing a scanner, the dispute is dispositively resolved)
- Proof of delivery (signed, photographed, or carrier-acknowledged) for each of the three packages
- The internal warehouse pick list showing which SKUs were placed in which package

If the merchant cannot produce these records, the merchant's representation that they shipped a $700 scanner cannot be supported. If they can produce them, and the records contradict their claim, the records themselves establish the fraud.

## 6. Public-record context

Creality has 67 complaints filed with the Better Business Bureau in the most recent three-year period. All 67 are documented as unanswered by Creality. The merchant is not BBB-accredited. The complaint categories include delivery issues, refund and return difficulties, and sales-and-advertising misrepresentations - the same categories implicated by the present dispute.

The bank can independently verify the public-record complaint pattern at the Better Business Bureau profile for Creality 3D, City of Industry, California location. The same pattern is reflected in public Trustpilot reviews for `creality.com` and `creality3dofficial.com`.

This context is offered not to substitute for the specific evidence in my own case (the items received, the network-traffic absence, and the shipping-pattern observations above), but to establish that the merchant operates with a documented public-record pattern of non-engagement with consumer disputes. The bank should weigh that context in evaluating Creality's eventual response to my dispute, particularly if Creality fails to substantively engage with the bank's evidentiary requests.

## 7. Attestation

I declare under penalty of perjury under the laws of the United States that the foregoing is true and correct to the best of my knowledge.

This affidavit is digitally signed below using my published PGP key (fingerprint `9267 A71E 3F0A 4EED 2F97 3F9B A3E2 52F2 4635 CC6C`). The signature allows the bank to verify that the document has not been modified after signing.

Executed this 17th day of June, 2026.

---

**Cardholder:** Jay Puckett (Reckoner)
**Organization:** Obsidian Watch Group
**Email:** investigations@obsidianwatch.org
**PGP fingerprint:** 9267 A71E 3F0A 4EED 2F97 3F9B A3E2 52F2 4635 CC6C
**Verification:** the PGP signature accompanies this document; bank may verify via any OpenPGP-compatible tool against the published public key at keys.openpgp.org or keyserver.ubuntu.com.
