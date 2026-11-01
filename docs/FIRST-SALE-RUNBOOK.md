# First-sale runbook — 5-minute verification

Use this when the **first genuine customer** pays. Do **not** create a second paid purchase just to diagnose failures.

Worker: `https://localfirst-migrator-delivery.localfirst-migrator.workers.dev`  
Payment Link ID: `plink_1UWksxDfRMA6MAW5PnIWuELQ`  
Private release: operator-known private GitHub downloads repo, tag `v1.0.0` (do not publish the repo name in customer-facing channels)

## 5-minute checklist

1. **Stripe payment succeeded**  
   Dashboard → Payments: status paid/complete for the new Checkout Session. Note session id (`cs_…`) privately — never paste into public chat/issues.

2. **Webhook received 2xx**  
   Developers → Webhooks → endpoint for `/stripe/webhook` → recent delivery: `checkout.session.completed` (or async success) with **2xx**. If 4xx/5xx, open delivery details (signature/secret mismatch is the usual cause).

3. **Customer redirect occurred**  
   Payment Link “After payment” must still be:  
   `https://localfirst-migrator-delivery.localfirst-migrator.workers.dev/?session_id={CHECKOUT_SESSION_ID}`  
   Confirm customer landed on **Payment confirmed** (ask them for a redacted screenshot without session query string if needed).

4. **Worker authorized session**  
   Customer can open Download. Failures: missing/malformed session, unpaid, wrong payment link, amount/currency mismatch → Worker returns deny (fail-closed). Check Cloudflare Worker logs for the request time **without** logging secret values.

5. **Private GitHub asset fetch succeeded**  
   If download fails after auth: check `GITHUB_DOWNLOAD_TOKEN` still valid, release `v1.0.0` still private with both assets present, and Worker health still reports `github-private-release`.

6. **Customer obtained archive**  
   Filename: `LocalFirst-Migrator-1.0.0-x86_64.tar.gz`

7. **Checksum available**  
   SHA-256 page/file matches:  
   `7d15b52011063f9a064716d34eb4cc8544e070ab9cb1df0641edc0d7ad47f3ee`

## Recovery without another charge

| Symptom | Recovery |
| --- | --- |
| Paid but no redirect | Fix Payment Link after-payment URL; send customer the fulfillment URL with their real `session_id` via a **private** channel (not GitHub Issues). |
| Redirect OK, download denied | Verify session is live+paid+correct plink/amount via Stripe Dashboard; confirm Worker secrets still set (`wrangler secret list` names only). |
| Webhook failing | Confirm `STRIPE_WEBHOOK_SECRET` matches the endpoint signing secret; resend event from Stripe Dashboard test/resend. |
| GitHub 401/404 from Worker | Refresh fine-scoped download token; confirm release assets; keep repo **private**. |
| Checksum mismatch reported | Do not improvise a new hash. Re-verify private release asset against pinned Worker `ARCHIVE_SHA256`. |

## What not to do

- Do not make the downloads repo public
- Do not paste `whsec_`, Stripe keys, or GitHub tokens into chat
- Do not ask the customer to post session IDs publicly
- Do not charge a second “test” purchase to debug
