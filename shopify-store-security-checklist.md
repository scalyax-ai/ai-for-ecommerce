# Shopify Store Security Checklist

**How to use this:** Copy this document, assign an owner to each section, and record evidence beside completed items.  
Work through the checks today, then review the monitoring log daily for the next few weeks.

Store: __________  
Checklist owner: __________  
Started: __________  
Next review: __________

## 1. Check notices and establish what applies

- [ ] Search owner, admin and former account-holder inboxes, including spam, for notices from Triple Whale.
- [ ] Verify any notice through the provider’s official website or an existing support channel before opening attachments or following login links.
- [ ] Save verified notices, support correspondence and relevant timestamps in a restricted incident folder.
- [ ] If notified, follow the instructions addressed to your store and assign someone to track completion.
- [ ] Separate confirmed information from unanswered questions. Do not treat forum posts or leaked-record claims as proof your store was affected.

**Triple Whale context:** Its supplied statement says impacted parties were notified and that no action is required on your Triple Whale account if you did not receive a notification. The remaining checks are general store security practices. [Triple Whale statement](https://x.com/triplewhale/status/2123848682646765890)

If you received a notice, ask through verified support:

> Please confirm which of our store’s data categories and connected credentials were affected, the relevant dates, any required actions, and where we should follow official updates.

## 2. Review installed apps and customer data access

- [ ] In Shopify admin, open **Settings > Apps**, then select each app.
- [ ] Review its permission details, personal data access, privacy policy and available security information.
- [ ] Record whether it can read customer names, email addresses, phone numbers, addresses, order history or spending.
- [ ] Record write permissions separately, especially access involving orders, refunds, discounts or store settings.
- [ ] Assign a business owner and a current purpose to every app.
- [ ] Before removing an app, check whether checkout, fulfillment, subscriptions, reporting or advertising depends on it.
- [ ] Uninstall apps you no longer use after resolving those dependencies.

Shopify documents where to review app permissions and security details in its [app management guide](https://help.shopify.com/en/manual/apps/managing-apps).

| App | Business owner | Purpose | Customer data accessible | Write access | Keep or remove | Completed |
|---|---|---|---|---|---|---|
| __________ | __________ | __________ | __________ | __________ | __________ | __________ |

**Meta ads check:** Include attribution tools, customer audience integrations, reporting connectors and tools that send purchase events. Record which Shopify and Meta assets each integration connects.

## 3. Request deletion from past apps

Uninstalling revokes app access, but does not confirm deletion of previously collected data. Shopify says it sends developers an erasure request after 48 hours; confirmation must come from the developer. [Shopify data access and deletion guidance](https://help.shopify.com/en/manual/apps/finding-choosing-apps)

- [ ] Review recently uninstalled apps, past trial accounts, billing records and integration emails.
- [ ] Contact each former provider through its verified support or privacy channel.
- [ ] Request deletion of store and customer data no longer required.
- [ ] Ask what must be retained, why, and for how long.
- [ ] Request written confirmation and track unresolved requests.

**Copy and send:**

> Subject: Data deletion request for [store domain]
>
> We previously used your app with [store domain] under [account email]. We uninstalled it or ended our trial on [date, if known].
>
> Please delete our store and customer data that you no longer need or are required to retain, including relevant exports and data held by subprocessors.
>
> Please confirm:
>
> 1. What data you held for our store.
> 2. What has been deleted and when.
> 3. Any retained data, its purpose, applicable retention requirement and deletion date.
> 4. How backup copies are handled and when they expire.
> 5. Whether any separate account closure or authorization revocation is needed.
>
> Please provide a request reference and written confirmation when complete.

| Provider | Request date | Reference | Follow-up date | Deletion confirmed | Retention exception |
|---|---|---|---|---|---|
| __________ | __________ | __________ | __________ | __________ | __________ |

Do not attach customer exports, passwords or API tokens to the request.

## 4. Secure accounts and connected credentials

### Staff access

- [ ] Review Shopify users, roles and collaborator access. Remove former staff and expired agency access.
- [ ] Reset staff passwords using each person’s own account settings. Use unique passwords stored in a password manager.
- [ ] Enable two-factor authentication wherever supported, including Shopify, Meta, email, SMS, fulfillment and the email accounts used for recovery.
- [ ] Review active sessions and sign out unfamiliar devices.
- [ ] Check recovery email addresses and phone numbers.
- [ ] Store recovery codes securely with restricted access.

### Keys, tokens and integrations

- [ ] List credentials used by analytics, advertising, email, SMS, warehouse and reporting tools.
- [ ] Identify who owns each credential, what it permits and every integration that uses it.
- [ ] Revoke unused authorizations.
- [ ] Rotate active keys and tokens through the issuing platform’s supported process. Prioritize credentials identified in a verified notice or showing suspicious use.
- [ ] Update dependent integrations and confirm they work before retiring the previous credential, where the platform supports overlap.
- [ ] For suspected active compromise, revoke affected access promptly and coordinate service restoration.
- [ ] Record credential identifiers and rotation dates only. Never put secret values in this checklist.

**Shopify custom apps:** Ask the developer to plan token replacement. Uninstalling and reinstalling can deregister webhooks and other integration resources that must be restored. [Shopify installation and token guidance](https://help.shopify.com/en/manual/apps/install-setup-apps)

### Meta ads access

In Meta Business Suite, open **Settings** for the correct business portfolio. Labels can vary.

- [ ] Review **People**, **Partners** and **System users**, where available.
- [ ] Check access to ad accounts, Pages, Instagram accounts, catalogs and datasets.
- [ ] Remove unknown or expired access and unnecessary administrator permissions.
- [ ] Require two-factor authentication for everyone where the portfolio setting is available.
- [ ] Have the integration owner replace relevant system-user or Conversions API tokens using Meta’s supported process.
- [ ] After changes, check Events Manager diagnostics and test events to confirm purchase tracking still arrives.
- [ ] Check for duplicate purchase events, unexpected campaigns, budget changes and unfamiliar billing activity.

| Integration | Credential identifier | Owner | Action | Completed | Function verified |
|---|---|---|---|---|---|
| __________ | __________ | __________ | __________ | __________ | __________ |

## 5. Prepare customers and support for phishing

- [ ] Give support examples of messages that use real order details to request payment, credentials or account access.
- [ ] Require identity verification through your established process before changing delivery addresses, account details or refunds.
- [ ] Do not accept a correct order number or mailing address as sufficient proof of identity.
- [ ] Tell customers how to contact your store independently.
- [ ] Publish a general phishing reminder if appropriate. Have incident-specific notices reviewed under section 6.

**Customer reminder template:**

> Security reminder from [store name]: Be cautious of unexpected messages about an order, delivery charge or refund, even when they contain accurate order details.
>
> Do not share passwords, login codes or full payment card details in a reply. To check a request, open our website yourself at [store domain] and use [verified support channel].
>
> If you receive a suspicious message claiming to be us, report it through that channel. Please hide sensitive information in any screenshot.

**Support response template:**

> Thank you for flagging this. Please do not reply, pay or open further links in that message.
>
> Contact us through [verified support channel] so we can check the request. If you already entered a password, change it through the official service and secure any account using the same password. If you entered payment details, contact your payment provider through its official channel.

- [ ] Record phishing reports without copying unnecessary personal data.
- [ ] Escalate repeated reports, unauthorized account changes or payment attempts to the checklist owner.

## 6. Assess notification duties promptly

- [ ] Assign a privacy or legal owner as soon as you learn of a possible incident.
- [ ] Record when your business became aware and what information was available then.
- [ ] Identify relevant jurisdictions based on your business, affected customers and applicable law.
- [ ] Assess the data involved, likely harm and protective steps.
- [ ] Determine whether customers, regulators or contractual partners must be notified.
- [ ] Record applicable deadlines, decisions, reasons and who approved them.
- [ ] Reassess when the provider supplies new information.

A provider’s notification does not automatically settle your store’s obligations. Ask a qualified adviser or the relevant regulator if unsure.

For example, UK guidance distinguishes reporting to the regulator from notifying affected people, with different risk thresholds and timing requirements. Use the [ICO breach guidance](https://ico.org.uk/pdb) only where applicable.

| Decision | Owner | Applicable deadline | Action and reason | Next review |
|---|---|---|---|---|
| __________ | __________ | __________ | __________ | __________ |

## 7. Monitor daily for the next few weeks

Assign one person to review and one backup.

| Area | Check for | If unexpected |
|---|---|---|
| Shopify access | New users, collaborators, permission changes or unfamiliar sessions | Verify with the owner; revoke unauthorized access |
| Orders | Unexplained edits, address changes, unusual discounts or order patterns | Review before fulfillment using your fraud process |
| Refunds | Unexpected refunds, cancellations or gift card activity | Verify the actor and preserve transaction details |
| Payments | Payout destination or billing changes | Escalate through verified platform support |
| Apps | New installations, permissions or integrations | Verify the installer and business purpose |
| Meta ads | Unknown campaigns, spend changes, new administrators or billing changes | Contain unauthorized activity and contact Meta support |
| Tracking | Missing or duplicate purchase events after credential changes | Have the integration owner investigate |
| Customer support | Messages using real order details to solicit money or codes | Preserve redacted examples and escalate patterns |

**Monitoring log:**

| Date and time | Reviewer | Finding | Evidence location | Action | Owner and next check |
|---|---|---|---|---|---|
| __________ | __________ | __________ | __________ | __________ | __________ |

If something looks wrong:

1. Preserve relevant notices, logs and screenshots in restricted storage.
2. Verify the activity with the responsible account owner.
3. Contain confirmed unauthorized access or transactions promptly.
4. Contact the platform through a verified channel.
5. Reassess customer risk and notification duties.

## Completion check

- [ ] Every app has an owner and a documented purpose.
- [ ] Unused access has been removed.
- [ ] Past-app deletion requests are confirmed or have a follow-up date.
- [ ] Account security and relevant credential changes are complete.
- [ ] Checkout, fulfillment and purchase tracking work after changes.
- [ ] Support has the phishing response instructions.
- [ ] Notification decisions and deadlines are documented.
- [ ] Daily monitoring has an owner and a next review date.

Outstanding actions: __________  
Responsible owner: __________  
Due date: __________
