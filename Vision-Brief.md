# Decision Memo: One premium customers can trust

**Date:** November 17, 2026  
**Author:** Samuel Ogunyemi  
**Decision area:** Day 2 — estimate and saved premium

## Context

When the app first connected to the quote service, the same customer details produced two different prices. The app showed $425 for an auto quote, while the service saved it at $450 per month. The difference came from two rate tables that had drifted apart while the app and service were being built separately.

## Options considered

1. **Keep the two rate tables as they were.** The app would remain quick, but customers could see one price and save another. That would undermine trust.
2. **Align the app’s rates with the service.** Customers would still get a quick estimate, and the saved quote would agree with it. The rates would still exist in two places, so they could drift again later.
3. **Make every estimate wait for the service.** This would give the app one source for pricing, but it would add a network dependency to every estimate and was beyond the agreed scope for this launch.

## Recommendation

Align the app’s rates with the service’s standardized rates: auto 90, home 135, and life 70. Keep the instant estimate for this launch, and treat the service as the source of truth for the premium saved to the database.

## Why

A fast estimate is useful only if the customer can trust the amount they see. Matching the estimate to the saved quote avoids an unpleasant surprise at the moment the customer chooses to keep their quote.

## What would change my mind

If the two rate tables drift again, or a later product decision requires rates to change frequently, I would recommend moving rate ownership to one centrally managed source before expanding the product.
