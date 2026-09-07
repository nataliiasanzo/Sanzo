# Data pull — 2026-09-07

**Status: FAILED — cycle continued on cached data** (`dashboard/data.json` still holds the Aug 27 pull; failed identically on one retry)

Console output of the pull step:

```
=== Pulling Instagram data via Apify ===
Incremental pull: last 60 posts, merging into 999 cached
FAILED: Apify 403 on /acts/apify~instagram-scraper/runs: {
  "error": {
    "type": "platform-feature-disabled",
    "message": "Monthly usage hard limit exceeded"
  }
}

Pull failed — continuing with cached data (digest will say so).
```

## Diagnosis — needs your action

Third consecutive failed pull (Aug 28, Aug 31, Sep 7), all with the same 403 `platform-feature-disabled` / "Monthly usage hard limit exceeded". **The new calendar month did NOT clear it**, so waiting won't fix this: either the Apify billing cycle hasn't rolled over yet, or the account's monthly usage hard limit is set at (or near) zero, or the plan itself is out of credit.

**To fix:** log into Apify Console → Billing → Limits, check the "monthly usage hard limit" and raise or remove it (or upgrade the plan / wait for the account's own billing-cycle reset date shown there). Until then, every weekly run will send the digest from the cached Aug 27 data with a stale-data warning.
