# Record of processing activities (GDPR art. 30): IRIS

**Internal. Do not publish.**

- Date: 2026-11-09
- Status: Draft for legal review
- Source of the table facts: `internal/privacy/registry.go`
- Other sources: `subprocessors.html`, `privacy-en.html` and `dpa-en.html` (Annex 1 and Annex 2), all in version 3 draft of 8 November 2026. Job periods were checked in `internal/jobs/` (`retention.go`, `identity_retention.go`).
- Note: `registry_test.go` fails when a migration adds a table that the registry does not name. So the registry has one entry for every table. Part C lists every entry.

How to read this record. The registry and the legal drafts are the only sources. Where a source does not state a fact, the text says `[TO BE VERIFIED: ...]`. No retention period, legal ground or sub-processor was added from outside these files.

Roles. IRIS (the "Operator") is controller for its customers' account data, users, sign-in records, billing, invitations, operator and audit records, support and reports (Part A). IRIS is processor, on behalf of each customer, for commenters, contacts and subscribers, conversations, consent records, suppressions, mail deliveries and events, webhook deliveries and broadcasts (Part B). The customer is a creator or a business and is the controller of that data.

---

## Part A. Art. 30(1): IRIS as controller

### A.1 Fields required by art. 30(1)

**(a) Controller name and contact.**
`[TO BE COMPLETED: operator name and contact, kept outside the repository]`

**(b) Purposes.**
- To provide the account, sign-in, sessions and the selected service.
- To manage invitations and access.
- To document the DPA acceptance.
- To keep an audit of customer and operator actions.
- To run the Instagram integration and to end it safely.
- To identify the sender in mail footers and on capture pages, and to configure the sending domain.
- To bill customers, keep tax and accounting records, and handle claims.
- To prepare account exports and to prove account deletion and Meta deletion requests.
- To answer support requests, complaints and rights requests.
- To keep the service secure and reliable (logs, counters, limits, health history).
- To stop a later account from using the sender address of a deleted account.

**(c) Categories of data subjects.**
- Customers and the representatives of customers that are legal entities.
- Invitees who have no account.
- Panel and legal-page visitors.
- People who contact IRIS.
- The staff of IRIS who use operator access.

**(c) Categories of personal data.**
- Account data: email, language, account name, settings, time zone, notification preferences.
- Sign-in data: email, one-time token hash, IP prefix. Session data: token hash, IP prefix, user agent, activity times.
- Invitation data: email, language, operator note, who added the invitation and when, expiry, acceptance state.
- DPA acceptance: version, time, IP prefix, user agent.
- Audit records: time, identifiers, IP prefix, browser, changed field names and non-personal values.
- Instagram connection: identifiers, username, account type, permissions, encrypted token, expiry.
- Sender identity: name, postal and contact email addresses, sending domain.
- Billing data: email, NIP, buyer details, Stripe customer, subscription, price and payment identifiers, purchased blocks and block lead quantities.
- Export and deletion records.
- Support correspondence: address, content, attachments, metadata.
- Request and error logs, identifiers, sender domain.
- Operator data: email, sessions, IP prefix, browser, operator handle and actions.
- Technical counters with account identifiers.
- A hash of a sender identifier after account deletion.

**(d) Categories of recipients.**
- Resend, for sign-in and other IRIS mail and for customer mail. AWS is the further processor of Resend.
- Cloudflare: proxy, TLS, DNS, Tunnel, public-image cache and operator Access. It sees transmitted data, IP addresses, full paths, forms, webhooks and cookies.
- OVHcloud: the operator mailbox and mail redirects. A VPS for the application and PostgreSQL is planned and not yet ordered.
- Stripe Payments Europe Ltd., for the customer's own billing. `[TO BE VERIFIED: applicable Stripe entity for the IRIS agreement, role for each service, countries and bases for transfers outside the EEA.]`
- Meta Platforms Ireland Ltd., an independent controller for data on its platform.
- GitHub Pages, which hosts the public legal pages and receives visit data such as IP addresses.
- Tailscale, which serves host administration. The deployment documentation says that it carries no customer data.
- Public authorities, where the law requires it.
- Accountants or other advisers: `[TO BE VERIFIED: actual use of accountants or other advisers, their roles and recipient scope; no such provider is assumed.]`

**(e) Transfers to third countries and safeguards.**
- Resend sends from AWS eu-west-1 (Ireland). According to the documentation used for the drafts, Resend holds account data and metadata in the USA. The drafts name Standard Contractual Clauses. `[TO BE VERIFIED: scope of data in the USA, current agreement, SCC module, further processors and supplementary measures.]`
- AWS infrastructure is in the EU and the USA according to the project documentation. `[TO BE VERIFIED: applicable AWS entity, locations and basis for onward transfers.]`
- Cloudflare runs a global network. No EU-only restriction is verified. `[TO BE VERIFIED: agreement and transfer basis for the IRIS account, including SCCs and supplementary measures; processing countries, remote access and retention.]` Reliance on the EU-US Data Privacy Framework has not been verified.
- OVHcloud mailbox: `[TO BE VERIFIED: country of mailbox storage, copies and service access, and whether mail involves transfers outside the EEA.]`
- Stripe: see (d).
- A database in France does not mean that all data stays in the EEA.

**(f) Retention.** See the "Retention" column of the table in A.2. The registry sets each period. The privacy policy states that the deletion jobs run on thresholds, and that scheduling, batches and locks can delay a deletion. `[TO BE VERIFIED: production settings and maximum delays.]`

**(g) Security measures (general description, from DPA Annex 2).**
- HTTPS for public traffic. HSTS for one year with subdomains outside development mode. Cloudflare ends TLS. The path from the host to Cloudflare uses Cloudflare Tunnel.
- Security headers: a strict Content-Security-Policy, no framing, nosniff, a referrer policy.
- Instagram access tokens and unsubscribe tokens are encrypted with AES-256-GCM. Keys can be rotated.
- Sign-in by single-use link. Authentication tables store hashes of sign-in and session tokens. Session cookies use HttpOnly and SameSite=Lax. CSRF protection applies.
- Account isolation: queries in the customer panel are scoped to the signed-in account. The account identifier does not come from the request body.
- Audit trail of customer and operator actions. IP truncated to /24 (IPv4) or /48 (IPv6) where recorded.
- Webhooks are accepted only with a valid signature.
- Operator access only through Cloudflare Access with a one-time PIN and a separate application session. Host administration uses Tailscale. The host does not expose the application or database port publicly.
- Minimisation and deletion: automatic deletion by the periods in the registry, erasure of a named person, account export, account deletion with proof.
- No external analytics, error tracking or application log collection.
- Not yet in place: monitoring and backups. `[TO BE VERIFIED: production measures before launching the VPS, disk and backup encryption, restoration, monitoring.]`

### A.2 Processing activities as controller

Legal grounds are those of `privacy-en.html` section 3: b is Art. 6(1)(b) GDPR (contract), c is Art. 6(1)(c) (legal obligation), f is Art. 6(1)(f) (legitimate interests). `privacy-en.html` itself marks the mapping of grounds `[TO BE VERIFIED: approval of basis mapping, balancing tests and specific laws supporting c.]`

| Activity | Data subjects | Data | Purpose | Legal ground | Tables | Retention | Recipients |
|---|---|---|---|---|---|---|---|
| A1 Account | Customers and their representatives | Email, language, account name, settings, time zone, notification preferences | Account service | b; f for representatives | `users`, `tenants` | For as long as the tenant (registry). Privacy policy: until account deletion | Resend, Cloudflare |
| A2 Sign-in | Account holders and people without an account who ask for a link | Email, one-time token hash, IP prefix | Send sign-in links, prevent abuse | b on the person's request; f for security | `sign_in_tokens` | 7 days after `expires_at` (job `identity_retention`). The privacy policy adds: token valid 15 minutes by default | Resend, Cloudflare |
| A3 Sessions | Customers | Token hash, IP prefix (/24 or /48), user agent, activity times | Authentication | b and f (access protection) | `sessions` | Deleted at `expires_at` (job `identity_retention`). The registry states no number. The privacy policy states a default maximum of 7 days | Cloudflare |
| A4 Invitations | Invitees without an account | Email, language, operator note, who added it and when, expiry, acceptance state | Access to the service | f (managing invitations and access) | `invitations` | 30 days after `lapsed_at` (job `identity_retention`). An unused invitation lapses at its expiry, or 180 days after it was added when it has none | Resend |
| A5 DPA acceptance | Customer representatives | Version, time, IP prefix, user agent | Document the conclusion of the DPA | c (documenting processing under Art. 28 GDPR); f (evidence and defence of claims) | `dpa_acceptances` (`dpa_versions` holds no personal data) | For as long as the tenant | None stated |
| A6 Customer audit | Customers and their users | Time, identifiers, IP prefix, browser, changed field names, non-personal values | Accountability and security | f (abuse detection, establishing actions) | `audit_events` | 730 days from `occurred_at` (job `registry_retention`) | None stated |
| A7 Instagram connection | Customers | Identifiers, username, account type, permissions, encrypted token, expiry | The requested integration | b | `social_accounts` | For as long as the tenant. Removing the connection removes the row (`connect.Remove`) | Meta (independent controller) |
| A8 Removed Instagram connections | Customers | Instagram identifier and dates | Find later webhooks and end subscriptions safely | f (safe disconnection and erasure handling) | `removed_instagram_accounts` | 90 days from `unsubscribed_at` (job `webhook_retention`). A row with no stamp has no age and stays until the unsubscribe succeeds | Meta |
| A9 Sender identity and sending domain | Customers and representatives | Name, postal and contact email addresses, sending domain | Identify the sender in footers and on capture pages, configure mail | b; f for representative details | `tenant_brands`, `sending_domains`, `sending_domain_tombstones` | `tenant_brands` and `sending_domains`: for as long as the tenant. `sending_domain_tombstones`: the registry states no retention. `[TO BE VERIFIED: maximum retention for residual domain-removal data.]` | Resend (domain), Cloudflare |
| A10 Customer content and settings | Customers | Campaigns, templates, images, lists, tags, links, settings | Provide the service | b for the customer's data (entrusted data of others: Part B) | `campaigns`, `campaign_variants`, `campaign_links`, `email_templates`, `links`, `lists`, `tags`, `media_images`, `settings` | `campaigns` and `media_images`: for as long as the tenant. The other tables: no retention in the registry; they go with the tenant by cascade, except `settings` (purge batch) | Cloudflare (public images in cache) |
| A11 Billing | Customers and their representatives | Email, NIP, buyer details, Stripe customer, subscription, price and payment identifiers, purchased blocks and lead quantities | Payments and invoicing | b (contract); c (tax and accounting records); f (claims) | `plan_addons`, `subscriptions`, `stripe_events` (`plans` and `addon_blocks` hold no personal data) | `plan_addons` and `subscriptions`: for as long as the tenant. `stripe_events`: 90 days from `received_at` (job `stripe_events_retention`). The Stripe customer and tax records stay at Stripe after account deletion. `[TO BE VERIFIED: specific laws, periods and starting points for invoice, correction, payment and retained Stripe data.]` | Stripe |
| A12 Exports and deletion proof | Customers | Export file, tenant identifier, steps and times, Meta deletion requests | Return of data and accountability | b (service); f (evidence); c where a GDPR duty is performed | `account_exports`, `account_deletions`, `data_deletion_requests` | `account_exports`: 24 hours from `expires_at`. `account_deletions`: 365 days from `finished_at`. `data_deletion_requests`: 365 days from `received_at`, never purged while still received (job `registry_retention`) | None stated |
| A13 Support, complaints and rights requests | People who contact IRIS | Address, content, attachments, metadata | Answer and handle cases | b for contractual support; f for other correspondence and claims; c for rights requests and legal duties | None in the registry (the OVHcloud mailbox) | `[TO BE VERIFIED: correspondence, request, complaint and claim periods, criteria and deletion from the OVHcloud mailbox.]` | OVHcloud |
| A14 Request and error logs | Visitors, customers | Request and error logs, identifiers, sender domain. Ordinary request logs hold the route pattern, status and duration, not a full token link | Diagnostics and protection | f (security and reliability) | None in the registry (Docker logs) | Up to 5 files of 10 MB per container, no established time limit. `[TO BE VERIFIED: maximum retention and log minimisation, including errors and provider logs.]` | Cloudflare (provider logs) |
| A15 Operator access | IRIS staff | Email, sessions, IP prefix, browser, operator handle, actions | Controlled support and security | f (control of privileged access) | `operator_sign_in_tokens`, `operator_sessions`, `operator_events` | `operator_sign_in_tokens`: 7 days after `expires_at`. `operator_sessions`: deleted at `expires_at` (the privacy policy states a maximum of 8 hours and 60 minutes idle). `operator_events`: 730 days from `occurred_at`, also after the customer deletes the account | Cloudflare Access, Resend |
| A16 Technical counters and health history | Customers (account identifiers) | State, codes, counts and class per account. The registry states that these tables hold no person | Service operation, limits, abuse prevention | f (reliability and abuse prevention) | `health_transitions`, `meta_calls`, `outbox_skips`, `rate_limit_buckets`, `circuit_breakers`, `account_polls`, `usage_events` | `health_transitions`: 730 days from `at`. `meta_calls`: 14 days from `at`. `outbox_skips`: 90 days from `hour`. `rate_limit_buckets` and `circuit_breakers`: 90 days from `removed_instagram_accounts.removed_at`. `account_polls` and `usage_events`: no retention in the registry | Meta (calls) |
| A17 Hash of a sender identifier | Deleted customers | SHA-256 of the sender slug and a time | Stop another account from reusing the sender address | f (preventing impersonation) | `tenant_slug_tombstones` | For ever (registry). `[TO BE VERIFIED: proportionality and any maximum retention for this hash.]` | None stated |

---

## Part B. Art. 30(2): IRIS as processor

### B.1 Fields required by art. 30(2)

**(a) Processor name and contact.**
`[TO BE COMPLETED: operator name and contact, kept outside the repository]`

**(a) Controllers on whose behalf IRIS acts.** Each IRIS customer (a creator or business that has an account and has accepted the DPA). The record of acceptance is in `dpa_acceptances`. `[TO BE VERIFIED: whether the record must hold the name and contact of each controller, and where.]`

**(b) Categories of processing carried out for each controller.**
- Collecting leads from comments on the controller's Instagram posts.
- Replying to commenters by private message and public reply.
- Creating contacts for commenters and collecting email addresses.
- Confirming and storing subscribers, with list and tag assignments.
- Recording consent, unsubscribes and suppressions.
- Sending the controller's emails and broadcasts, and measuring delivery and link clicks.
- Receiving and storing raw webhooks.
- Preparing the account export, and erasing a named person's data on the controller's instruction.

**(c) Transfers to third countries and safeguards.** The same facts as Part A, (e). The sub-processor list covers the entrusted data: Resend (with AWS as its further processor) and Cloudflare. A planned OVHcloud VPS is listed as a planned sub-processor. All are marked `[TO BE VERIFIED]` in `subprocessors.html` for entity, locations and transfer basis. Meta is an independent controller and not a sub-processor. Stripe is not a sub-processor of entrusted data: the code does not send individual commenters' or subscribers' data to Stripe.

**(d) Security measures.** The same as Part A, (g). They are described in DPA Annex 2.

### B.2 Processing activities as processor

The customer decides the purpose and the legal ground and gives its own notice to data subjects (`privacy-en.html` section 4). IRIS processes the data on the customer's documented instructions (DPA section 4). Because of this, the table has no legal ground column.

| Activity | Data subjects | Data | Purpose | Tables | Retention | Sub-processors and recipients |
|---|---|---|---|---|---|---|
| B1 Contacts and subscribers | Commenters, people who message the account, people who give an email address | Instagram identifier, username, email and its normalized form, confirmation status, list and tag assignments, encrypted unsubscribe token | Create contacts, collect and confirm email addresses, store subscribers | `contacts`, `list_members`, `contact_tags` | `contacts`: 90 days, counted from the greatest of `updated_at`, `lead_conversations.updated_at` and `automation_executions.evaluated_at`, only for a contact that never held an address and has no tag, live-list membership, consent, delivery, suppression or broadcast recipient row (job `contact_retention`). Every other contact lives with the tenant. `list_members` and `contact_tags`: as long as the contact | Resend, Cloudflare |
| B2 Receipt of comments and messages | Commenters and message senders | Raw webhook bodies with comment and message text, post and comment identifiers, evaluation results | Receive events from Meta and match them to the controller's rules | `webhook_deliveries`, `webhook_delivery_accounts`, `processed_events`, `automation_executions` | `webhook_deliveries`: 90 days from `received_at` (job `webhook_retention`). `webhook_delivery_accounts`: 90 days, counted from the delivery's `received_at`. `processed_events`: 45 days from `first_seen_at`. `automation_executions`: 90 days from `evaluated_at` (job `pipeline_retention`) | Cloudflare; Meta (independent controller) |
| B3 Replies | Commenters and message senders | Outgoing private message and public reply text, links, recipient identifier | Reply to commenters | `outbound_intents` | 30 days from `updated_at` (job `pipeline_retention`) | Meta |
| B4 Capture conversations | People who give an address by message or on a capture page | Conversation state, verification attempts and method, keyed digest of the six-digit code, hash of the capture-page token | Verify addresses | `lead_conversations`, `capture_tokens` | `lead_conversations`: with the contact; 90 days from `updated_at` for a row with no contact (job `registry_retention`). `capture_tokens`: 30 days from `expires_at` (job `capture_retention`) | Resend, Cloudflare |
| B5 Consent and suppression | Contacts and subscribers | Consent scope, channel, time, key, recorded wording, language, source identifiers. Suppressed address, reason and date | Document consent, honour unsubscribes, prevent further sends | `consent_events`, `suppressions` | `consent_events`: as long as the contact. `suppressions`: permanent in the registry, deleted with the tenant by cascade | None stated |
| B6 Mail deliveries and events | Recipients of the controller's email | Recipient address, delivery identifiers, delivery events, bounce and complaint diagnostics | Send the controller's email, measure delivery | `email_deliveries`, `mail_events` | `email_deliveries`: 90 days from `created_at` (job `capture_retention`). `mail_events`: 90 days from `received_at` (job `registry_retention`); deleted with the account, except events the Service could not assign to an account, which have no account key and stay until that clock ends | Resend (AWS as further processor) |
| B7 Broadcasts and clicks | Recipients and people who click tracked links | Broadcast recipient rows; click counts per link and UTC day, with no recipient and no send (the link in a message carries the link id alone; the IP address and the user agent are used in memory only and are not stored) | Send broadcasts, measure clicks | `broadcast_recipients`, `link_click_days`, `broadcasts` | `broadcast_recipients`: as long as the contact. `link_click_days`: as long as its link or the tenant; a person's erasure keeps it. `broadcasts`: no retention in the registry | Resend, Cloudflare |
| B8 Controller content | People whose data is in content or images the controller supplies | Campaign, message, capture-page and image content, to the extent it holds personal data | Provide the service | `campaigns`, `campaign_variants`, `campaign_links`, `email_templates`, `links`, `lists`, `tags`, `media_images` | `campaigns` and `media_images`: as long as the tenant. The other tables: no retention in the registry | Cloudflare (public images in cache) |
| B9 Account export | Contacts and subscribers named in the export | Export zip with contacts, consent records, suppressions, audit events, campaigns, templates, broadcasts, brand (with the confirmed notice copy), billing and content restrictions | Return of data | `account_exports` | 24 hours from `expires_at` (job `registry_retention`) | None stated |

---

## Part C. Every table in the registry

Source: `internal/privacy/registry.go`, in the registry's order. "Role" is IRIS's role for the table. A registry class `none` is written as "no personal data". "Retention" repeats the registry. "Erasure" gives what a per-person erasure does, then what happens when the tenant is deleted. For a table with no erasure kind in the registry, the cell says so.

| # | Table | Role | Whose data | Retention (registry) | Erasure (registry) |
|---|---|---|---|---|---|
| 1 | `contacts` | processor | A person who is not a customer; found by email, Instagram user id, handle | For a fixed age: 90 days, from the greatest of `updated_at`, `lead_conversations.updated_at`, `automation_executions.evaluated_at`. The 90 days apply only to a contact that never held an address and has no tag, live-list membership, consent, delivery, suppression or broadcast recipient row; every other contact lives with the tenant. Job `contact_retention` | Person: delete. Tenant: explicit delete in the deletion sequence (purge batch) |
| 2 | `lead_conversations` | processor | A person who is not a customer; found by contact id, Instagram user id, email | For a fixed age: 90 days from `updated_at`, the sweep for rows with `contact_id IS NULL`. A conversation with a contact goes with its contact. Job `registry_retention` | Person: delete. Tenant: cascade |
| 3 | `consent_events` | processor | A person who is not a customer; found by contact id, Instagram user id | For as long as the contact | Person: cascade through `contact_id`. Tenant: cascade |
| 4 | `capture_tokens` | processor | A person who is not a customer; no lookup key | For a fixed age: 30 days from `expires_at`. Job `capture_retention` | Person: cascade through `conversation_id`. Tenant: cascade |
| 5 | `suppressions` | processor | A person who is not a customer; found by email | Permanent: never deleted. Reason: an address that opted out or bounced must stay refused; kept on RODO art. 17(3)(b) and art. 21 | Person: detach (kept with the personal link cut); an erasure sets `contact_id` NULL and diagnostic ''. Tenant: cascade |
| 6 | `email_deliveries` | processor | A person who is not a customer; found by email, contact id | For a fixed age: 90 days from `created_at`. Job `capture_retention` | Person: delete. Tenant: explicit delete in the deletion sequence (purge batch) |
| 7 | `mail_events` | processor | A person who is not a customer; found by email | For a fixed age: 90 days from `received_at`. Job `registry_retention` | Person: delete (found through the tenant's `email_deliveries`, by `provider_message_id` and by delivery id, and by the tenant and the recipient address). Tenant: explicit delete in the deletion sequence (purge batch); a row with no `tenant_id` (an event the Service could not assign to an account) stays until the retention clock removes it |
| 8 | `broadcast_recipients` | processor | A person who is not a customer; found by contact id | For as long as the contact | Person: cascade through `contact_id`. Tenant: cascade |
| 9 | `link_click_days` | processor | A person who is not a customer; no lookup key. A link, a UTC day and a count of clicks; no column names a recipient or a send | For as long as the tenant; goes with its link | Person: keep (no subject key finds a row). Tenant: cascade |
| 10 | `list_members` | processor | A person who is not a customer; found by contact id. Which of the tenant's lists a contact is on | For as long as the contact | Person: cascade through `contact_id`. Tenant: cascade |
| 11 | `contact_tags` | processor | A person who is not a customer; found by contact id. Which of the tenant's tags a contact carries | For as long as the contact | Person: cascade through `contact_id`. Tenant: cascade |
| 12 | `automation_executions` | processor | A person who is not a customer; found by Instagram user id, handle | For a fixed age: 90 days from `evaluated_at`. Job `pipeline_retention` | Person: delete. Tenant: explicit delete in the deletion sequence (purge batch) |
| 13 | `outbound_intents` | processor | A person who is not a customer; found by Instagram user id | For a fixed age: 30 days from `updated_at`. Job `pipeline_retention` | Person: delete. A pending or uncertain (`send_unknown`) row naming the id is cancelled and deleted with the terminal rows. A leased row is marked, not cancelled: a pump holds it and the message may already be at Meta. The mark turns every later return to pending into a cancel, and stops the dispatch stamp, a resend and a replay. A row already sent stays until the 30-day retention. Tenant: cascade |
| 14 | `processed_events` | processor | A person who is not a customer; found by Instagram user id | For a fixed age: 45 days from `first_seen_at`. Job `pipeline_retention` | Person: delete. Tenant: explicit delete in the deletion sequence (purge batch) |
| 15 | `webhook_deliveries` | processor | A person who is not a customer; found by Instagram user id, email | For a fixed age: 90 days from `received_at`. Job `webhook_retention` | Person: delete. Tenant: explicit delete in the deletion sequence (purge batch) |
| 16 | `webhook_delivery_accounts` | processor | A person who is not a customer; no lookup key. Goes with its delivery | For a fixed age: 90 days, from `webhook_deliveries.received_at`. Job `webhook_retention` | Person: cascade through `delivery_id`. Tenant: explicit delete in the deletion sequence (purge batch) |
| 17 | `sign_in_tokens` | controller | A person who is not a customer (a person who asks for a sign-in link); found by email | For a fixed age: 7 days from `expires_at`. Job `identity_retention` | Person: keep. No tenant key, so no per-tenant erasure can find a row; it is gone seven days after expiry. Tenant: no tenant key, the retention clock removes it |
| 18 | `invitations` | controller | A person who is not a customer (an invitee); found by email | For a fixed age: 30 days from `lapsed_at`. Job `identity_retention`. A removed or lapsed row is deleted 30 days after it lapses; an unused row lapses at its expiry, or 180 days after it was added when it has none | Person: keep. The invite list is an address with no tenant key, so a per-tenant erasure cannot find a row; an invitee's request is served by `iris invite remove --forget`. Tenant: explicit delete in the deletion sequence (purge batch) |
| 19 | `operator_sign_in_tokens` | controller | IRIS staff (operator). An operator's own address; no tenant key | For a fixed age: 7 days from `expires_at`. Job `identity_retention` | Keep (gone seven days after expiry). Tenant: the retention clock removes it |
| 20 | `operator_sessions` | controller | IRIS staff (operator). Session with its `ip_prefix` and `user_agent` | For a fixed age counted from `expires_at`; the registry gives no number; deleted at expiry. Job `identity_retention` | Keep. Tenant: the retention clock removes it |
| 21 | `operator_events` | controller | IRIS staff (operator). What an operator did, by handle; never exported | For a fixed age: 730 days from `occurred_at`. Job `registry_retention` | Keep. Tenant: outlives it on purpose (no foreign key to the tenant) |
| 22 | `account_exports` | controller | A person who is not a customer by registry class `subject`; no lookup key. The export zip of the tenant | For a fixed age: 24 hours from `expires_at`. Job `registry_retention` | Person: detach. The tenant's ready exports are expired at erasure: zip NULL, `expires_at` now. Tenant: outlives it (no foreign key; the deletion sequence builds the export before the tenant row goes and the zip stays downloadable 24 hours after it) |
| 23 | `users` | controller | The customer; found by email. The customer's own sign-in, not a subject | For as long as the tenant | Keep. Tenant: cascade |
| 24 | `sessions` | controller | The customer. Holds the customer's `ip_prefix` and `user_agent` | For a fixed age counted from `expires_at`; the registry gives no number; deleted at expiry. Job `identity_retention` | Keep. Tenant: cascade |
| 25 | `dpa_acceptances` | controller | The customer. The record that the customer accepted the DPA | For as long as the tenant | Keep. Tenant: cascade |
| 26 | `audit_events` | controller | The customer. `changes` holds field names and non-personal values only | For a fixed age: 730 days from `occurred_at`. Job `registry_retention` | Keep. Tenant: explicit delete in the deletion sequence (purge batch) |
| 27 | `social_accounts` | controller | The customer; found by Instagram user id, handle. The customer's own connection, removed by `connect.Remove` | For as long as the tenant | Keep. Tenant: cascade |
| 28 | `removed_instagram_accounts` | controller | The customer; found by Instagram user id. The customer's own removed connection | For a fixed age: 90 days from `unsubscribed_at`. Job `webhook_retention`. A row with no stamp has no age and stays. Until the unsubscribe succeeds it stays, also after a data-deletion request from Meta. The row goes with the tenant, or with a new connect of the id by any tenant | Keep. The tenant's person erasure and its account deletion read it to find the webhook deliveries that name the id and arrive after the removal. Tenant: cascade |
| 29 | `tenant_brands` | controller | The customer's own postal address and contact address | For as long as the tenant | Keep. Tenant: cascade |
| 30 | `tenants` | controller | The customer. The root; deleting it is the cascade | For as long as the tenant | Keep. Tenant: cascade |
| 31 | `sending_domains` | controller | The customer. Removed by `sendingdomain.Remove`, which also deletes the provider's domain | For as long as the tenant | Keep. Tenant: cascade |
| 32 | `media_images` | controller | The customer: the tenant's logo and pictures | For as long as the tenant; kept while the tenant exists, because mail already sent links them by id | Keep. Tenant: cascade |
| 33 | `data_deletion_requests` | controller | The customer. The proof of a deletion Meta asked for; no tenant key | For a fixed age: 365 days from `received_at` (12 months), so the status link works while Meta can ask; never purged while still received. Job `registry_retention` | Keep. Tenant: outlives it |
| 34 | `campaigns` | controller | The customer's own configuration; found by handle | For as long as the tenant | Keep. `erase --handle` reports how many campaigns name the handle in `ignore_handles`. Tenant: cascade |
| 35 | `campaign_variants` | no personal data | The tenant's copy; exported inside `campaigns.json` | None stated | None stated. Tenant: cascade |
| 36 | `campaign_links` | no personal data | URLs the tenant wrote; exported inside `campaigns.json` | None stated | None stated. Tenant: cascade |
| 37 | `email_templates` | no personal data | The tenant's content, no person | None stated | None stated. Tenant: cascade |
| 38 | `broadcasts` | no personal data | The tenant's content | None stated | None stated. Tenant: cascade |
| 39 | `links` | no personal data | URLs the tenant wrote | None stated | None stated. Tenant: cascade |
| 40 | `lists` | no personal data | The names the tenant gave its lists; who is on one is `list_members` | None stated | None stated. Tenant: cascade |
| 41 | `tags` | no personal data | The names the tenant gave its tags; who carries one is `contact_tags` | None stated | None stated. Tenant: cascade |
| 42 | `usage_events` | no personal data | Counts | None stated | None stated. Tenant: cascade |
| 43 | `account_polls` | no personal data | Cursors and counters; goes with its account | None stated | None stated. Tenant: cascade |
| 44 | `outbox_skips` | no personal data | Counts per hour | For a fixed age: 90 days from `hour`. Job `pipeline_retention` | None stated. Tenant: explicit delete in the deletion sequence (purge batch) |
| 45 | `health_transitions` | no personal data | States and Meta codes; history only, no decision reads it after the fact | For a fixed age: 730 days from `at`. Job `registry_retention` | None stated. Tenant: explicit delete in the deletion sequence (purge batch) |
| 46 | `meta_calls` | no personal data | Class, status and codes; the path names Meta object ids, not people | For a fixed age: 14 days from `at`. Job `meta_calls_retention` | None stated. Tenant: explicit delete in the deletion sequence (purge batch) |
| 47 | `rate_limit_buckets` | no personal data | Token counts, no person. A removal keeps the account's rows while its protection window lasts, so a connect of the same Instagram account takes them over. The app-wide rows have no account and stay | For a fixed age: 90 days from `removed_instagram_accounts.removed_at`. Job `meta_calls_retention` | None stated. Tenant: no tenant key, the retention clock removes it |
| 48 | `circuit_breakers` | no personal data | Breaker state, no person. A removal keeps the account's row while its protection window lasts, so a connect of the same Instagram account takes it over. The global row has no account and stays | For a fixed age: 90 days from `removed_instagram_accounts.removed_at`. Job `meta_calls_retention` | None stated. Tenant: no tenant key, the retention clock removes it |
| 49 | `settings` | no personal data | Switch keys; `updated_by` is an operator name | None stated | None stated. Tenant: explicit delete in the deletion sequence (purge batch). Tenant and suspension keys go in the purge, account keys in `connect.Remove` |
| 50 | `oauth_state_nonces` | no personal data | Random nonces, no tenant key | None stated | None stated. Tenant: outlives it |
| 51 | `dpa_versions` | no personal data | The DPA's texts, shared by every tenant | None stated | None stated. Tenant: outlives it |
| 52 | `subprocessors` | no personal data | Company names, shared by every tenant | None stated | None stated. Tenant: outlives it |
| 53 | `sending_domain_tombstones` | no personal data | A business domain, and either the provider's id or the times of a creating row whose create may have reached the provider with the answer lost; the job and the reconciliation deleting the provider's domain read it after the tenant is gone | None stated | None stated. Tenant: outlives it |
| 54 | `tenant_slug_tombstones` | no personal data | A SHA-256 of a deleted tenant's sender slug and a time, no tenant key. The registry says the hash is pseudonymous, not anonymous: the slug is the folded local part of a sign-in address, and a list of common names reverses it | Kept for ever (no retention field) | None stated. Tenant: outlives it |
| 55 | `account_deletions` | no personal data | Tenant id, steps and times: the proof of a deletion, no tenant key | For a fixed age: 365 days from `finished_at` (12 months once done). Job `registry_retention` | None stated. Tenant: outlives it |
| 56 | `plans` | no personal data | Shared seed, the catalog every tenant resolves against | None stated | None stated. Tenant: outlives it |
| 57 | `addon_blocks` | no personal data | Shared seed, the catalog every tenant resolves against | None stated | None stated. Tenant: outlives it |
| 58 | `plan_addons` | controller | The customer. The extra lead blocks the customer bought | For as long as the tenant | Cascade through `tenant_id`. Tenant: cascade |
| 59 | `subscriptions` | controller | The customer. Our copy of the customer's subscription; the Stripe customer itself is kept at Stripe, because its invoices are tax records | For as long as the tenant | Cascade through `tenant_id`. Tenant: cascade |
| 60 | `stripe_events` | controller | The customer. Stripe's payload holds the customer's email and tax id | For a fixed age: 90 days from `received_at`. Job `stripe_events_retention` | Cascade through `tenant_id`. Tenant: cascade |
| 61 | `river_*` | no personal data | River's own tables. A job's args (`template_test_email`'s `to`) go with the deletion sequence's purge, which deletes the tenant's jobs in every state but running. `account_unsubscribe` carries no tenant id and outlives it on purpose: its args hold the Instagram id and the sealed token while it waits to send the unsubscribe Meta needs, which lasts as long as a switch or a breaker refuses the call. River keeps the finished row with those args for 24 hours after it completes and 7 days after it is discarded (River's default retention, which applies to every kind alike) | None stated | None stated. Tenant: outlives it |

**Count check.** Entries found in the registry (`Registry` slice of `internal/privacy/registry.go`): 61. Rows in the Part C table: 61. The two counts match. The 61st entry, `river_*`, names a group of tables with a wildcard and is counted as one entry.

---

## Part D. Open points

### D.1 Slots marked `[TO BE VERIFIED]` or `[TO BE COMPLETED]` in this record

1. Part A.1 (a) and Part B.1 (a): `[TO BE COMPLETED: operator name and contact, kept outside the repository]` (two slots).
2. Part A.1 (d): the Stripe entity, roles for each service, countries and transfer bases.
3. Part A.1 (d): the use of accountants or other advisers.
4. Part A.1 (e): Resend and AWS (data in the USA, agreement, SCC module, further processors, supplementary measures, applicable AWS entity, onward transfers).
5. Part A.1 (e): Cloudflare (agreement, transfer basis, processing countries, remote access, retention, DPF).
6. Part A.1 (e): the OVHcloud mailbox (country, copies, access, transfers outside the EEA).
7. Part A.1 (f): production settings and maximum delays of the deletion jobs.
8. Part A.1 (g): production measures, disk and backup encryption, restoration, monitoring.
9. Part A.2 intro: approval of the basis mapping, balancing tests and the specific laws supporting ground c.
10. A9: maximum retention of residual domain-removal data (`sending_domain_tombstones`).
11. A11: laws, periods and starting points for invoice, correction, payment and retained Stripe data.
12. A13: periods and criteria for correspondence, requests, complaints and claims, and deletion from the OVHcloud mailbox.
13. A14: maximum retention and minimisation of logs.
14. A17: proportionality and maximum retention of the sender-identifier hash.
15. Part B.1 (a): whether the record must hold the name and contact of each controller, and where.

### D.2 Disagreements between the registry and the legal drafts

1. **Class of `broadcasts`, `email_templates`, `campaign_variants`, `campaign_links`, `links`, `lists`, `tags`.** `internal/privacy/registry.go`: class `none`, no person. `dpa-en.html` (Annex 1, types of data): campaign, message, capture-page and image content is entrusted data "to the extent it contains personal data". This record lists these tables in Part B (B7, B8) and in Part C as "no personal data". Needs a decision.
2. **Role of `media_images`.** Registry: class `customer` (the tenant's logo and pictures, so IRIS as controller). `dpa-en.html` Annex 1: images supplied by the controller are entrusted data of people shown in them, and `privacy-en.html` section 3 says other people's data in images is entrusted. This record shows `media_images` in Part A (A10), in Part B (B8) and as controller in Part C.
3. **Role of `campaigns`.** Registry: class `customer`, "the customer's own configuration". `dpa-en.html` section 4: campaign settings, keywords and reply text are the controller's instructions, and `privacy-en.html` section 3 gives ground b for the customer's own data. Not a conflict of facts, but the two documents do not use the same split.
4. **`tenant_slug_tombstones`.** Registry class `none`, while its own reason says the hash is "pseudonymous, not anonymous". `privacy-en.html` section 3 uses the same word, "pseudonymous", and keeps it indefinitely. A class `none` is not consistent with this.
5. **`river_*`.** Registry class `none`, while its own reason says `account_unsubscribe` args hold the Instagram id and the sealed token, and they stay 24 hours after completion or 7 days after discard. `privacy-en.html` section 7 and `dpa-en.html` section 12 mention the pending jobs as a deletion exception, with a `[TO BE VERIFIED]` on their maximum duration.
6. **`rate_limit_buckets` and `circuit_breakers`.** Registry: 90 days from `removed_instagram_accounts.removed_at`; tenant deletion is "duration" (the retention clock, not the account deletion). `privacy-en.html` section 3 (technical counters): "account-linked data is removed with the account" and gives no period for these two tables.
7. **`suppressions`: retention basis.** Registry gives a ground (RODO art. 17(3)(b) and art. 21) and the retention "permanent". `dpa-en.html` Annex 1 marks "retention basis and proportionality, references to Articles 17(3)(b) and 21 GDPR" as `[TO BE VERIFIED]` and says the list is deleted with the account. The registry also deletes it with the tenant by cascade, so the facts agree, but the ground is unverified in the legal drafts.
8. **`suppressions`: what stays after a person's erasure.** Registry: `contact_id` set NULL and diagnostic ''. `privacy-en.html` section 4 and `dpa-en.html` Annex 1 also say the broadcast identifier (`broadcast_id`) may remain. The registry does not mention it.
9. **`contacts`: the clock of the 90 days.** Registry: the greatest of `updated_at`, `lead_conversations.updated_at` and `automation_executions.evaluated_at`. `privacy-en.html` section 4 and `dpa-en.html` Annex 1: from the last comment or message, taking later contact or conversation updates into account. Neither draft names the automation executions.
10. **`contacts`: holds that stop the 90 days.** Registry: tag, live-list membership, consent, delivery, suppression, broadcast recipient row. The drafts add a list in its 10-second restoration window, an address or verification in a conversation, awaiting a code and a valid unused capture link. The registry comment does not name these.
11. **Sessions.** Registry: `sessions` and `operator_sessions` are deleted at `expires_at`, with no number. `privacy-en.html` section 3 states a default maximum of 7 days for a customer session, and a maximum of 8 hours and 60 minutes idle for an operator session. The numbers are not in the registry.
12. **Year length.** Registry comment: a year is 365 days and 24 months is 730 days. The drafts say "12 months" and "24 months". Agreement of values: `audit_events`, `operator_events` and `health_transitions` 730 days (24 months); `account_deletions` and `data_deletion_requests` 365 days (12 months).
13. **Processing with no registry table.** Support correspondence (A13) and request and error logs (A14) are processing in `privacy-en.html` and `dpa-en.html` (Docker log rotation), but no registry entry names them, because they are not database tables. Their retention is `[TO BE VERIFIED]` in the drafts.
14. **Registry class `subject` for controller tables.** `sign_in_tokens`, `invitations` and `account_exports` have class `subject` (a person who is not a customer). IRIS is the controller of them according to `privacy-en.html`. This record assigns the role "controller" in Part C. `account_exports` holds entrusted data inside the zip and is also listed in B9.

Items 1 to 6 and 14 change what the record says about roles. They need a decision of the owner or the lawyer before the record is final.
