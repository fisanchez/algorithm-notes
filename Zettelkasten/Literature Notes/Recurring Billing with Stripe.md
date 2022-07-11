---
title: Recurring Billing with Stripe
created_at: Wednesday 22nd June 2022
uuid: 1655905475
tags: #refinement
---

## Epic
-   Assets will be identified as subscriptions
-   Assets will have asset feature metadata that identify them as recurring billing assets
-   For initial delivery for Fall Rush, 2022, we will support credit card payments through Stripe for recurring billing subscription purchases
    -   PayPal support is out of scope
    -   Apple Pay/Stripe Wallet transactions are out of scope
    -   Watchman/Financial Aid transactions are out of scope
-   We are building the following two Stripe features:
    -   Apple Pay via Stripe (VST-26899)
        -   This is true at a code level, even though the feature itself will not be used immediately for recurring payments
    -   Saved Payments via Stripe (VST-28109)
-   Pricing will be as normal through Manage / Catalogs

This feature will leverage Stripe's subscription management functionality and work as follows:
-   A user purchases a recurring payment asset
-   Stargate saves payment information for that purchased asset
    -   NB: This means the Stripe payment_intent and payment_method, not raw card data
		<span style="color:red">
		When do we create a new payment intent using the payment_method?
		</span>
-   On a regular schedule, based on asset duration (e.g. 30 days):
    -   Stripe bills the customer for the next interval
    -   Stripe sends Stargate a webhook indicating the user has been charged
    -   Stargate extends the license
    -   Stargate sends a transactional email to the user
-   Subscriptions will be managed via Stripe's end-user facing subscription management UI
    -   Updating billing method
    -   Subscription cancellation
    -   Users will be given an authenticated redirect from Account Center, through Stargate, to Stripe
-   Stargate will handle refunds since this work happens through Stripe, however, Jiffy and Manage will need to review and potentially adjust refund qualification rules
    -   e.g. 14 days after initial purchase and some percent unread
    -   Subsequent billing will only allow cancellation of billing, but not prorate a refund


## VST-46305
This will create a new `AssetMetaData` table that will be a JSON based table and allow to store data like accessibility data in the database vs making api calls at request time.

We will primary use this for asset features which are like feature flags for assets.

## VST-46306
Creates a sideque job to make asset metadata calls to get the data and store the data

## VST-46307
Make the asset feature metadata ingestion part of the catalog import process

## VST-46308
PDP displays recurring payment assets

## VST-46309
We want to accept any incoming Stripe subscription webhooks even if we don't currently do anything with them.

## VST-46310
Create new payment data modeling to support repeat billing.

## VST-46364
Creates a recurring payment feature flag


**Payment Authorizor**
creates payment intent

**TLDR**
- Subscription will be handled by Stripe's UI
- Stargate will handle refunds
- Stargate saves `payment_method` and `payment_intent` from purchased asset








## References
[[06212022 Tuesday]]