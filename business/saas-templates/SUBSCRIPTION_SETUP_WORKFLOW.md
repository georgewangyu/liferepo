---
doc_schema: "doc-frontmatter-v1"
doc_id: "liferepo/business/saas-templates/SUBSCRIPTION_SETUP_WORKFLOW"
doc_type: "business_doc"
doc_status: "active"
title: "Subscription Setup Workflow"
description: "Reusable default workflow for adding subscriptions to a SaaS product without overbuilding billing architecture."
memory_eligible: true
memory_priority: "medium"
doc_tags:
  - "domain:business"
  - "domain:saas"
  - "domain:billing"
  - "visibility:public"
  - "type:business_doc"
---
# Subscription Setup Workflow

Reusable default for products that need monthly or annual subscriptions.

This exists because "we'll add billing later" is usually how teams end up with
fragmented auth, checkout, entitlement, and support flows.

The working lesson from the SnackVoice rollout was simpler:

1. decide the entitlement policy first
2. keep billing on the website
3. make every client consume server entitlement state
4. test the full lifecycle before launch

## Default Architecture

Use this as the baseline unless a real constraint says otherwise:

1. Website owns Stripe Checkout and Billing Portal.
2. Stripe webhooks update subscription state in durable backend storage.
3. Backend exposes one entitlement source of truth for signed-in users.
4. App clients fetch entitlement and gate features from that response.

Practical rule:

- web handles money
- backend handles truth
- clients handle UX

Avoid:

- license-key logic as the primary paid-access system
- separate billing logic per client
- treating Stripe status as a frontend-only concern

## Recommended Build Order

### 1. Lock Product Policy Before Code

Write down the non-code decisions first:

- plans and price IDs you expect to sell
- free tier or trial policy
- what `active`, `past_due`, `canceled`, and `grace` mean in product behavior
- refund/cancel posture
- quota semantics if usage limits exist
- outage/offline grace policy

If this is not written down, engineering will invent policy accidentally.

### 2. Start From a Proven Starter, Then Simplify

Do not hand-roll auth plus checkout plus webhooks from a blank file if a
well-understood starter already solves the boring parts.

Good default:

- start from a proven open-source web starter that already demonstrates
  account auth, Stripe checkout, and customer mapping

What to copy:

- auth/session shape
- customer lookup or creation flow
- hosted checkout pattern
- success/cancel redirect handling

What not to copy blindly:

- extra pricing surfaces you do not need yet
- multi-product complexity
- team billing, usage metering, or admin features you are not shipping

## Implementation Sequence

### Phase A. Web Billing Foundation

Build the billing spine on the web first:

1. create Stripe product and recurring price objects
2. create hosted checkout session in `mode=subscription`
3. attach checkout to a signed-in account email
4. add Billing Portal session endpoint
5. persist Stripe customer, subscription, and checkout-session references

Why:

- hosted Stripe surfaces reduce PCI and edge-case burden
- account-linked billing is easier to reconcile than purchase-token hacks

### Phase B. Webhook and Storage Hardening

Before calling billing "done", add:

- webhook handling for checkout completion and subscription lifecycle updates
- idempotency / duplicate-event protection
- durable storage for users, subscriptions, and processed webhook events

Minimum states to track:

- user ID
- email
- Stripe customer ID
- plan ID
- subscription status
- current period end
- last verified timestamp

### Phase C. Entitlement API

Expose one backend endpoint that tells the product what the account can do now.

That response should be enough for a client to decide:

- paid or free
- blocked, active, or grace
- quota remaining if applicable
- when the entitlement was last verified

This is the key separation:

- Stripe state is billing truth
- entitlement response is product truth

### Phase D. Client Integration

Only after the entitlement API is stable should app clients wire billing UX:

- sign in
- fetch entitlement on launch and periodically
- show current plan and quota state
- open billing portal through backend
- gate paid-only features from entitlement response

For desktop or mobile apps, do not put Stripe billing logic in the native app
unless store-policy forces it. Prefer browser-first auth and purchase handoff.

### Phase E. Lifecycle QA

Run the actual subscription lifecycle before launch:

1. create account
2. start checkout
3. complete purchase in Stripe test mode
4. verify webhook persistence
5. verify entitlement becomes active
6. open billing portal
7. cancel or fail payment
8. verify downgrade behavior
9. replay webhook to confirm idempotency

If a support issue would require manual database surgery, the workflow is not
finished yet.

## Lessons Worth Keeping

### 1. Account-based entitlement beats license-key thinking

If the product has multiple clients or repeated usage over time, tie paid access
to an account and entitlement API. It is easier to reason about than serial
numbers or ad hoc unlock files.

### 2. Billing policy is product design, not implementation detail

Weekly quota reset rules, free-tier behavior, cancellation timing, and outage
grace windows all become support problems if they are left implicit.

### 3. Browser-first purchase and auth flows reduce desktop complexity

For non-store desktop apps, letting the website own sign-in, verification, and
checkout avoids duplicated credential and billing UI inside the app.

### 4. Idempotency is not optional

Webhook retries and repeated user actions will happen. Deduplicate writes and
keep a processed-event record from day 1.

### 5. Add support runbooks before public rollout

Document how to diagnose:

- "I paid but still look free"
- "my cancellation did not stick"
- "payment recovered but my app is still locked"

## Default Checklist

- written pricing + entitlement policy
- recurring Stripe price IDs created
- hosted checkout working for signed-in user
- billing portal route working
- webhook events persisted idempotently
- entitlement endpoint implemented
- client plan/quota state wired
- lifecycle integration test scripted
- support runbook written

## When To Deviate

Break this workflow only when a real constraint forces it, for example:

- App Store / Play billing policy requires native purchase flow
- enterprise invoicing is the real primary sales motion
- multi-seat/team billing is required on day 1

If you deviate, write the reason explicitly and record the new source of truth.
