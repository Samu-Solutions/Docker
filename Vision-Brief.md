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
# Stakeholder Status Update: Evergreen Quote

**To:** Priya Ramanathan, Project Sponsor  
**From:** Samuel Ogunyemi  
**Date:** November 9, 2026

## What shipped today

- The REST quote routes are assembled. I applied the provided premium-calculation fix, and all seven local tests pass.
- I checked the REST endpoints for listing, retrieving, creating, and rejecting invalid quotes.

## What slipped (and why)

- Renters coverage is deferred to a follow-up delivery. It is more than a dropdown change: it needs an approved rate and coordinated updates across validation, premium calculation, seed data, tests, GraphQL, and the website.
- GraphQL wiring and verification are still in progress.

## What's next (tomorrow)

- Finish wiring and verifying GraphQL, then continue with the container and CI work.
- Check the CI result before treating the delivery as ready to merge.

## What I need from you

Please confirm that renters coverage should be planned for a follow-up delivery, and identify when you’d like to review the proposed priority and approve a renters rate. I recommend proceeding this week with the current `node:22-alpine` base image: the finding is moderate, the API is not internet-exposed this week, and the patched tag is expected next week. We’ll document the risk and revisit the patched tag when it is available.
