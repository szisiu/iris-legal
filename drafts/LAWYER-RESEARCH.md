# IRIS: research file for the lawyer and the accountant

Internal. Do not publish. Written 2026-11-09 by an AI agent from statutes it knows, the
project's earlier research and web searches. No lawyer or tax adviser has checked it. It is a
starting brief: each item says what the law seems to require, how sure the author is, the
safe default that the drafts use until a professional answers, and who must confirm it.

Confidence: **high** = the rule is read from a primary source or is long settled;
**medium** = the rule is known but its fit to IRIS is a judgement; **low** = recalled or from
secondary sources only.

Facts about the operator used here: sole proprietorship in Poland, active VAT payer, sells to
businesses and consumers, one online service paid by card through Stripe in recurring periods.

Companion files: `LAWYER-NOTES-v3.md` (questions per document, with code sources) and the
bracketed slots inside each draft.

## Part 1. Questions for the lawyer

### 1.1 The ten questions of the outline

| # | Question | What the research says | Confidence | Default in the drafts |
|---|---|---|---|---|
| 1 | Sole traders for whom the contract has no professional character: exclude them, or give every customer the withdrawal right? | Since 2021 a sole trader who buys outside their trade has the consumer's withdrawal right and unfair-terms protection (Consumer Rights Act art. 7aa; Civil Code art. 385^5). The seller cannot contract out of it. IRIS also sells to plain consumers, so the consumer regime must work in full anyway. | high on the rule | Every customer gets the consumer-grade terms. No declaration of professional character is required. |
| 2 | Change, price, renewal, court and liability-cap clauses against the unfair-terms list (Civil Code art. 385^1 to 385^3); one cap for the Regulamin and the DPA | A cap on liability for personal injury or for intentional harm is void. A one-sided change of price or terms without a stated reason and a termination right is a grey-list clause. A forum clause against a consumer does not bind. A cap in a DPA cannot limit a data subject's claims (GDPR art. 82). | medium | Closed list of change reasons, 30 days' notice, right to end the contract, no forum clause for consumers, the cap excluded for consumers where the law forbids it. |
| 3 | Comment-to-DM consent chain: is the first DM a service reply or commercial information? What must the wording be under PKE art. 398? Tracked links under art. 399? | Art. 398 PKE requires prior consent for marketing through automated systems and end devices. A reply that a person asked for with a keyword comment is arguably a requested service message, but only when it carries no promotion beyond the requested material. Click measurement through a redirect link that carries an identifier is within art. 399: EDPB Guidelines 2/2023 (paragraphs 49 to 51) say that a tracking link sent by e-mail or message is storage on, and access to, the device. Marketing consent under art. 398 does not cover it. | medium to low | The first DM carries only the requested material and the consent sentence. Marketing needs the separate second consent and a confirmed address. Links carry no per-recipient identifier unless the recipient gave prior consent to measurement; the product's click measurement must be checked against this. |
| 4 | The creator's notice at the first DM, and how long a commenter who never replied may be kept | GDPR art. 14(3)(b): at the first communication at the latest. The code deletes a contact with no address 90 days after the last activity, unless a tag or a list holds it. | high on art. 14; medium on 90 days | Template `end-user-notice.html`; product field for the creator's notice is issue #44. |
| 5 | Hosting service or online platform under the DSA; what must be live | IRIS stores customer content and shows some of it publicly at the customer's request (sign-up pages, images). Dissemination to the public is a minor, ancillary feature of the main service, which points to "hosting service" and not "online platform" (art. 3(i) and recital 13). Even as a platform, a micro or small enterprise is exempt from the platform section (art. 19), with one exception: art. 24(3), the duty to give the coordinator or the Commission the number of active recipients on request. Live duties for hosting: art. 11, 12, 14, 16, 17, 18; art. 15 does not apply to micro or small enterprises. The Polish act (Dz.U. 2026 poz. 1296) is in force since 2026-11-06. | high on the dates; medium on the classification | Treated as hosting. `report.html` and `acceptable-use.html` were published on 2026-11-09. |
| 6 | Data Act switching rules (Regulation (EU) 2023/2854, art. 23 to 31) | They cover "data processing services", which reads on SaaS. Applies from 2025-09-12; switching charges must end by 2027-01-12. Duties: contract terms on switching, a notice period of at most 2 months, a transition period of 30 days, export of the customer's data. | medium | The Regulamin has a switching section; the 24-hour export file is not presented as the whole procedure. |
| 7 | Which address a sole trader publishes | UŚUDE art. 5 and the Consumer Rights Act art. 12 require the name, the address of the business and an e-mail address. For a sole trader that is the registered address of the business, even when it is a home. A virtual office address is lawful only when it is the registered address. | high | The drafts carry the registered address. The pages published on 2026-11-09 carry no identity by the owner's decision; that is an open gap. |
| 8 | Withdrawal-function directive (EU) 2023/2673 and the price-information rules | The directive requires an online "withdraw from contract" function for distance contracts, applied from 2026-06-19. Whether the Polish implementing act is in force was not confirmed (sources of mid-2026 disagree). | low on the Polish state | Offer withdrawal by e-mail and state it; plan an in-product function (see Part 3). |
| 9 | Minimum age | Instagram allows 13. The Polish age for consent to information-society services is 16 (GDPR art. 8 with the Polish act). A contract with a person under 18 needs a guardian's consent to be safe. | high on the ages | Customers must be adults. The creator notice has a slot for minors. IRIS does not check age. |
| 10 | Does the repeal of the hosting chapter of UŚUDE (from 2026-11-06) change the Regulamin? | The liability shield now comes directly from DSA art. 6. References to UŚUDE art. 14 must go. | medium | The drafts cite the DSA only. |

### 1.2 The three questions of 2026-11-08

| # | Question | What the research says | Confidence | Default |
|---|---|---|---|---|
| 11 | Is one line under the sign-in button enough to show agreement to the Regulamin, with no tick box (#465)? | Contract terms bind when the customer could read them before the contract (Civil Code art. 384). A tick box is not required by statute, but it is the usual proof. Consent to marketing or to data processing can never be bundled into that line. For consumers, the terms must also be given on a durable medium (e-mail) after the contract. | medium | One line plus a stored record of the version accepted (#381) plus the terms by e-mail. |
| 12 | Is a cookie banner necessary when every cookie is strictly necessary (#54)? | PKE art. 399 exempts storage that is necessary to provide the service the user asked for. Information is still required, consent is not. | medium to high | No banner; a cookie notice. A banner becomes necessary the day analytics or marketing scripts arrive. |
| 13 | Does the tick box for the DPA stay necessary? | GDPR art. 28(9) requires the DPA "in writing, including in electronic form". Any provable acceptance works; a tick box with a stored version is the strongest proof. | medium | Keep the tick box. |

### 1.3 Questions found on 2026-11-09

| # | Question | What the research says | Confidence | Default |
|---|---|---|---|---|
| 14 | DSA art. 12(1): is a second electronic contact method necessary? Who is a "recipient": customers only, or also subscribers? | The text says recipients must be able to choose the means of communication. One e-mail address gives no choice. | medium | E-mail only today; a report form is issue #475. |
| 15 | Does an automatic deliverability suspension need a DSA art. 17 statement of reasons? | Art. 17 covers restrictions imposed because content is illegal or breaches the terms. A suspension for high bounce rates is arguably a technical measure, but the policy treats it as a breach signal. | low | Treat it as covered: the suspension mail should state the facts and the way to contest. Today it states neither. |
| 16 | May the block on an address outlive the erasure of the person and the end of the contract with the customer? | GDPR art. 17(3)(b) and art. 21(3) support keeping a minimal suppression record. The code deletes all suppressions when the customer's account is deleted. | medium | Keep on person erasure; delete with the account. |
| 17 | The hash of the sender name kept without a time limit | A hash of a business sender name is weakly personal at most; "no time limit" still needs a justification under the storage-limitation rule. | low | Kept; slot in the deletion page. |
| 18 | Is the published DSA page lawful with no operator identity? | UŚUDE art. 5 and DSA art. 11 and 12 expect an identifiable provider. | high that it is a gap | Publish the identity with the Regulamin. |
| 19 | Must the operator have an electronic delivery address? | Sole traders entered in CEIDG before 2025 had to hold an e-Doręczenia address from 2026-10-01 (entry in the address base by 2026-09-30), per several sources of 2026. No fine for the delay was reported, but official letters can be deemed delivered. | medium (secondary sources) | Owner step, urgent: check on biznes.gov.pl and set it up. |
| 20 | Other acts to rule out | European Accessibility Act (services to consumers from 2025-06-28): micro enterprises that provide services are exempt. NIS2: micro and small entities are generally out of scope. Platform-to-business regulation: IRIS is not an intermediation service. AI Act: no AI feature today. | medium | No action; re-check when the business grows or features change. |

## Part 2. Document checklist

| Document | Required by | For whom | State |
|---|---|---|---|
| Regulamin | UŚUDE art. 8; Consumer Rights Act art. 12 | Customers | Draft v1 |
| Pre-contract information and order summary | Consumer Rights Act art. 12, 17 | Consumers | Not built (Part 3) |
| Withdrawal notice and model form | Consumer Rights Act art. 12(1)(9), annexes 1 and 2 | Consumers | Not written |
| Confirmation of the contract on a durable medium | Consumer Rights Act art. 21 | Consumers | Not built |
| Complaints procedure | UŚUDE art. 8(3)(4) | Customers | Inside the Regulamin, § 10 |
| Privacy policy | GDPR art. 13, 14 | Customers, visitors, invitees | Draft v1 |
| Cookie notice | PKE art. 399 | Visitors | Draft v1 |
| Data processing agreement and sub-processor list | GDPR art. 28 | Customers | Draft v1 |
| Record of processing | GDPR art. 30 | Internal | Draft (`record-of-processing.md`) |
| Breach register and procedure | GDPR art. 33(5) | Internal | Not written |
| Transfer assessments for non-EEA sub-processors | GDPR art. 44 to 46 | Internal | Not written |
| Creator notice template | GDPR art. 13, 14 (creator's duty) | Recipients | Draft |
| Acceptable-use policy | DSA art. 14; contract | Customers | Published 2026-11-09 |
| DSA contact point and report route | DSA art. 11, 12, 16 | Everyone | Published 2026-11-09 |
| Data deletion page | Meta Platform Terms | Customers, recipients | Draft; the old page is still public |
| Security page | Customer trust; not a legal duty | Customers | Not written (#467) |

A data protection officer is not required at this scale (GDPR art. 37). A data protection
impact assessment is worth a written one-page screening, because the service messages people
at scale on behalf of customers (art. 35); confidence low on whether a full assessment is due.

## Part 3. Checkout: consumer rules and proposed wording

### 3.1 The rules

- **Withdrawal.** A consumer can withdraw from a distance contract within 14 days (Consumer
  Rights Act art. 27). IRIS is a digital **service** supplied over time, not one-off digital
  content. For a service the right is lost only when the service is fully performed (art.
  38(1)(1)), which a running plan never is inside 14 days. The waiver for digital content
  (art. 38(1)(13)) therefore does not fit a plan. Confidence: medium to high.
- **Start before the 14 days end.** The seller may start at once only on the consumer's
  express request (art. 15(3), art. 21(2)). A consumer who then withdraws pays for the part
  used, in proportion (art. 35). Without that request the seller cannot charge for the days
  used. The same statement must hold the consumer's acknowledgment that the right of
  withdrawal ends on full performance (art. 21(2)); for a running plan that moment does not
  come inside 14 days, but the acknowledgment is part of the procedure. This request is the
  tick box below.
- **Trial.** A free trial with no card creates no payment duty; the rules bite at the first
  paid order.
- **Order button.** The button must say that the order means a duty to pay, in words such as
  "zamówienie z obowiązkiem zapłaty" (art. 17(3)). Otherwise the contract is not concluded.
  Stripe Checkout's button text must be checked against this; the label can be configured
  within limits. Confidence: high on the rule, low on what Stripe allows.
- **Before the order** the consumer must see: the main features, the total price with VAT,
  the billing period, that the plan renews until cancelled, how to cancel, the withdrawal
  right, the seller's identity (art. 12, art. 17(1)).
- **After the order** the seller sends the confirmation with these terms on a durable medium,
  for example e-mail (art. 21(1)).
- **Renewal and price changes.** A renewal at a new price needs prior notice and a free way
  out. Card-scheme rules ask the same for recurring charges: amount, frequency, and how to
  cancel, shown at sign-up and in the receipt.
- **Strong customer authentication.** The first card payment is authenticated (3-D Secure).
  Later charges are merchant-initiated and exempt, provided the first one set up the mandate.
  Stripe handles this.
- **Price reductions.** When a discount is announced, the lowest price of the 30 days before
  it must be shown (price-information act art. 4(2)). No duty when no discount is shown.
- **No pre-ticked boxes** for anything that costs extra (art. 10).

### 3.2 Proposed wording, Polish (governs)

Required tick box, consumers and sole traders with consumer rights:

> Proszę o rozpoczęcie świadczenia usługi przed upływem 14 dni na odstąpienie od umowy.
> Wiem, że jeśli odstąpię od umowy w tym terminie, zapłacę za okres, w którym korzystam
> z usługi, proporcjonalnie do ceny planu. Przyjmuję do wiadomości, że po pełnym wykonaniu
> usługi tracę prawo odstąpienia od umowy.

Line above the pay button (no tick box):

> Plan [NAZWA] kosztuje [KWOTA] zł brutto za [miesiąc / rok]. Odnawia się automatycznie na
> kolejny okres, a opłatę pobieramy z karty, dopóki nie zrezygnujesz. Zrezygnować możesz
> w każdej chwili w ustawieniach konta; plan działa do końca opłaconego okresu. Składając
> zamówienie, akceptujesz [Regulamin] i [Zasady dopuszczalnego użycia]. Informacje o danych
> podaje [Polityka prywatności].

Button: **Zamawiam z obowiązkiem zapłaty**

Withdrawal notice for the confirmation mail:

> Masz prawo odstąpić od umowy w terminie 14 dni od jej zawarcia bez podania przyczyny.
> Wystarczy, że przed upływem terminu wyślesz oświadczenie na adres support@irisapp.pl albo
> użyjesz funkcji odstąpienia w ustawieniach konta. Możesz użyć wzoru formularza, ale nie
> jest to obowiązkowe. Zwrócimy płatność w ciągu 14 dni, tym samym sposobem. Jeżeli na Twoją
> prośbę usługa zaczęła działać wcześniej, potrącimy kwotę proporcjonalną do okresu
> korzystania.

### 3.3 Proposed wording, English (translation)

> I ask you to start the service before the 14-day withdrawal period ends. I understand that
> if I withdraw in that period, I pay for the time I use the service, in proportion to the
> price of the plan. I acknowledge that I lose the right of withdrawal when the service is
> fully performed.

> The [NAME] plan costs PLN [AMOUNT] including VAT per [month / year]. It renews
> automatically for the next period, and we charge your card until you cancel. You can cancel
> at any time in the account settings; the plan runs to the end of the paid period. By
> ordering you accept the [Terms] and the [Acceptable-use policy]. The [Privacy Policy] says
> how we use data.

Button: **Order and pay**

> You can withdraw from the contract within 14 days of its conclusion, without a reason.
> Send a statement to support@irisapp.pl or use the withdrawal function in the account
> settings before the period ends. You can use the model form, but you do not have to. We
> refund the payment within 14 days, by the same method. If the service started earlier at
> your request, we keep the amount in proportion to the time of use.

### 3.4 What the product needs

The tick box and the line at checkout, a stored record of both with a timestamp and the text
version, the confirmation mail, a withdrawal function, and a proportional refund routine.
None exists today. For a business customer with a tax number the tick box can be skipped
only if the lawyer accepts a way to tell protected sole traders apart; the safe default is to
show it to everyone.

## Part 4. Tax and invoices (for the accountant)

Everything here is confidence **medium** unless marked; tax rules change and the operator's
own facts decide.

### 4.1 Where VAT is due

| Customer | Rule | Invoice |
|---|---|---|
| Poland, business or consumer | Polish VAT, 23% | Polish invoice; to a consumer on request |
| Other EU country, business with a valid EU VAT number | Place of supply is the customer's country (VAT act art. 28b). No Polish VAT; the customer accounts for it | Invoice with "odwrotne obciążenie" (reverse charge). The operator must be registered as an EU VAT payer (VAT-UE) and file the summary return |
| Other EU country, consumer | Electronic services are taxed in the consumer's country (art. 28k). Exception: while total cross-border sales of such services to EU consumers stay at or under EUR 10,000 (PLN 42,000) net in this and the previous year, Polish VAT applies | Above the limit: register for the One Stop Shop (OSS) in Poland and pay each country's VAT through one quarterly return, or register in each country |
| Outside the EU, business | Outside the scope of Polish VAT | Invoice marked "NP"; local rules of the customer's country may apply |
| Outside the EU, consumer | Not taxed in Poland; some countries (for example the United Kingdom, Norway, Switzerland) tax foreign digital sellers, some from the first sale | To verify per country, or do not sell there |

To decide where a consumer is, EU rules ask for two pieces of evidence that do not conflict
(billing address, card country, IP address). One piece is enough only when three conditions
are met: such sales are not over EUR 100,000 in the current and in the preceding calendar
year, and the evidence comes from a person involved in the supply other than the seller and
the customer, for example the payment provider (Implementing Regulation 282/2011 art. 24b,
24f). The customer's own statement of address is not enough alone.

### 4.2 A flow that fits the code

1. Checkout collects the country, the billing address and, for a business, the tax number
   (the code already enables tax-ID collection).
2. An EU VAT number is checked in VIES. Stripe Tax validates EU numbers; keep the result and
   the time as evidence. An invalid number means the sale is treated as a consumer sale.
3. Stripe Tax computes the rate (the code has a switch for automatic tax). It needs the
   operator's registrations entered in Stripe: Poland, and OSS when used.
4. The webhook for a paid invoice triggers the Polish invoice. A Stripe invoice or receipt is
   not by itself a Polish VAT invoice unless it carries all required fields; most Polish
   sellers issue the invoice from an invoicing program that is fed by the webhook.
5. The invoice goes to KSeF where required (4.3) and to the customer by e-mail.
6. Refunds and proportional withdrawals produce a correcting invoice.
7. Monthly: JPK_V7; quarterly: the OSS return when registered; the EU summary return for
   reverse-charge sales.

The add-on checkout sends no tax settings today (issue #453).

### 4.3 KSeF

- Mandatory for most sellers from 2026-04-01. The smallest sellers (invoices of at most PLN
  10,000 gross a month) are exempt until 2026-12-31; full duty and penalties from 2027-01-01
  (several sources of 2026; confirm on ksef.podatki.gov.pl).
- Invoices to consumers are outside the duty; they may be issued the old way. Confidence low.
- Invoices to foreign businesses are issued in KSeF and also delivered to the buyer in an
  agreed way, because the buyer has no access to KSeF. Confidence low.
- Stripe does not send invoices to KSeF. An invoicing program with a KSeF connection, or an
  own integration, is needed.

### 4.4 Other points for the accountant

- **Cash register.** Sales to consumers normally need a fiscal cash register. An exemption
  exists for services paid in full through a bank or payment institution where the records
  show which sale the payment was for; whether it covers electronic services sold by IRIS
  must be confirmed. Confidence low. This matters from the first consumer sale.
- **Stripe fees.** Stripe's fees are a service bought from an EU company (Ireland): import of
  services, reverse-charged by the operator.
- **Currency.** Sales in PLN avoid exchange-rate rules on invoices.
- **Records.** Tax records are kept for 5 years from the end of the year in which the tax was
  due; OSS records for 10 years.
- **Moment of the tax point** for a recurring service: the end of each billing period, or the
  payment when it comes first.

## Part 5. Cyber Resilience Act and security law

Regulation (EU) 2024/2847 covers products with digital elements placed on the EU market. A
service offered only online is not such a product; it is covered only as the "remote data
processing" part of a product that the same maker sells. IRIS ships no software to customers.
Reporting duties start 2026-09-11 and the main duties 2027-12-11, for those in scope.
Confidence: medium that IRIS is out of scope. Security duties that do apply come from GDPR
art. 32 and from the DPA, Annex 2.

## Part 6. Who verifies what, and when

| Item | Who | When |
|---|---|---|
| e-Doręczenia address (1.3, #19) | Owner | Now; the date has passed |
| Cash register and consumer invoices (4.4, 4.3) | Accountant | Before the first paid consumer sale |
| OSS limit, VAT-UE registration, VIES routine (4.1, 4.2) | Accountant | Before the first sale outside Poland |
| KSeF path (4.3) | Accountant | Receiving purchase invoices through KSeF: now, the duty applies from 2026-02-01 to every business. Issuing: before 2027-01-01, earlier if monthly invoices pass PLN 10,000 |
| Checkout wording and the start-now request (Part 3) | Lawyer | Before the first paid consumer sale |
| Withdrawal function (question 8) | Lawyer, then a build | With the checkout work |
| DSA classification and the published pages (questions 5, 14, 15, 18) | Lawyer | First item of the hand-off (#234) |
| Consent chain and first DM (question 3) | Lawyer | Before marketing features are promoted |
| Unfair terms and the cap (question 2) | Lawyer | Before the Regulamin is published |
| Sub-processor entities and transfers | Owner (contracts), lawyer | Before the DPA is published |
| Mailbox owner and answer times (#158) | Owner | Now; published pages name the mailboxes |
