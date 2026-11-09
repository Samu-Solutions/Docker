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
# Risk Register

| # | Risk | Owner | Likelihood (L/M/H) | Impact (L/M/H) | Mitigation | Trigger to escalate |
|---|---|---|---|---|---|---|
| R1 | The API may return a successful response while calculating an incorrect premium. Before the provided fix, the test caught a `$0.35` result where `$400` was expected. | Delivery Lead (coordinate); Engineering team (route owner) | M | H | Run `npm test` after relevant assembly or configuration changes and before requesting merge. Keep the premium-calculation test in the validation loop. | A premium-related test fails, or the API returns an unexpected premium after the fix. |
| R2 | The database may retain a quote created with the incorrect pre-fix premium, even though the route code has been corrected. | Delivery Lead (coordinate); Engineering team (data owner) | M | M | Record the possibility of stale test/demo data. Use the lab’s seed reset before the cluster demonstration and verify the data used for that demo. | An incorrect quote appears in a demonstration or is mistaken for valid current data. |
| R3 | Configuration may be inconsistent—for example, the API’s service name or sponsor-approved rates may not match the agreed values. | Delivery Lead; Sponsor for decisions | M | H | Confirm the sponsor’s official name and rate decision, update only the specified configuration values, restart after changing `.env`, and verify a known quote response. | Sponsor values are unknown or disputed, or the health response or premium check does not match the agreed values. |
| R4 | GraphQL may not be fully mounted or may behave differently from REST, leaving partner access unverified. | Delivery Lead (coordinate); Engineering team (GraphQL owner) | M | M | Confirm the module is wired at the provided markers. Test the list query, lookup query, and create mutation in `/explorer`; confirm a created quote appears through REST. | The explorer is unavailable, a required query or mutation fails, or REST and GraphQL return inconsistent quote data. |
| R5 | CI status is currently unknown, so a failing workflow or unverified test result could delay the pull request and merge. | Delivery Lead (coordinate); Engineering/CI owner | M | H | Enable the provided workflow, inspect the Actions run and logs, and use green CI as the merge gate. Do not treat a local pass as proof that CI passed. | The CI run is red, does not start, or has not completed before the planned merge. |
| R6 | An instructor inject may change priorities or consume time needed for the remaining delivery work. | Delivery Lead | M | M | Reprioritize the project board after the inject, record what moved and why, and communicate the next step and any specific help needed. | The inject blocks a critical path item or the revised plan threatens the delivery goal. |
| R7 | Working solo creates a capacity and review risk: one person must assemble, verify, document, and communicate the work. | Delivery Lead; Sponsor for priority decisions | M | M | Keep scope to the provided assembly steps, prioritize the required path, and raise tradeoffs early rather than adding optional work. | A required milestone is at risk, or the remaining work cannot fit the available time without a scope decision. |

## How I’ll use this register

I’ll review the risks during daily planning and again after each instructor inject. I’ll update likelihood, mitigation, and escalation triggers as the delivery progresses, and use the register to raise decisions or blockers with the sponsor rather than allowing them to surface at the final review.
