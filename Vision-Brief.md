# Evergreen Quote: Vision Brief

## Product

**Name:** Evergreen Quote API  
**Delivery week:** Phase 3 capstone  
**Delivery Lead:** Samuel Ogunyemi  
**Engineering team:** _Add repository link_  
**GitHub Project board:** _Add board link_

## Who is the customer?

Our customers are people looking for a quick, clear insurance quote, along with the websites and partner systems that help them get one. A customer may be comparing coverage, returning to a quote they started earlier, or using another channel such as an agent or partner application. Those experiences need the same dependable quote information instead of each channel calculating or storing it differently.

## What pain does Evergreen Quote remove?

Today, a quote can be calculated on a page, but it is difficult to treat that quote as something the customer or another system can reliably come back to. Evergreen Quote turns that one-time calculation into a shared service. It stores quotes, applies the same validation and premium rules each time, and makes the information available through REST and GraphQL. This gives customers a more consistent experience and gives our websites and partners one dependable source for quote information.

## What does “good” look like at the end of the week?

By the end of the week:

- A customer or partner can create a quote and receive a valid premium.
- Existing quotes can be found again instead of disappearing after the first calculation.
- The website and partner systems can use the same quote data through REST or GraphQL.
- Invalid requests are rejected clearly before they create bad data.
- The API passes its tests, runs in a container, and is demonstrated on a local Kubernetes cluster with three replicas.
- The work is reviewed, merged to `main`, and supported by a complete delivery package.

## What are we explicitly not doing this week?

- We are not building a completely new insurance application.
- We are not adding customer accounts, login, payments, or authentication.
- We are not deploying a production system to AWS or EKS.
- We are not completing a live S3 deployment unless the instructor approves it within the schedule.
- We are not rewriting or redesigning the engineering team’s supplied code. We are assembling, testing, and preparing it for delivery.

## How will we know it worked?

- The required tests pass locally and CI is green on the merged change.
- REST and GraphQL return consistent quote information.
- The same service works locally, in Docker, and behind the Kubernetes Service.
- The pull request is merged and the delivery package is complete.

----------------
# Decision Memo: Keep Renters Coverage Out of This Week’s Delivery

**Date:** Tuesday, November 9, 2026  
**Author:** Samuel Ogunyemi  
**Decision area:** Scope tradeoff after Inject #1

## Context

A partner aggregator asked us to make renters coverage quotable through the API by Thursday. It sounds like one more dropdown choice, but our morning checks showed that the API rejects unsupported quote types. Supporting renters would mean more than changing the dropdown: we would need an approved rate and updates to validation, seed data, tests, GraphQL, and the website. Adding that work now could put the agreed delivery goal at risk.

## Options considered

1. **Add renters coverage this week.** This could meet the partner’s request sooner. But the work crosses several parts of the product, the renters rate has not been approved, and we would need to reduce or delay other planned work to make room.

2. **Keep this week’s scope and plan renters for a later delivery.** This protects the current goal and gives us time to agree on the rate and plan the related changes. The tradeoff is that the partner will not be able to quote renters coverage this Thursday.

## Recommendation

I recommend keeping renters coverage out of this week’s delivery and recording it as a prioritized follow-up. We should finish and verify the agreed API delivery first, then schedule renters once the sponsor confirms the rate and the team can plan the full set of changes.

## Why

A quote is only useful if its premium is approved and consistent across the API, GraphQL, and customer-facing site. Adding an unapproved rate to meet a date could give the partner an answer that looks complete but is not trustworthy. Protecting quote accuracy and the delivery goal is more important than treating this as a small dropdown change.

## What would change my mind

I would reconsider if the sponsor approves a renters rate and confirms by Wednesday morning which planned work should move to make room—without compromising the required tests, CI, or Thursday delivery review.
