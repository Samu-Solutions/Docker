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
# Go / No-Go: Merge Decision

**Date / time:** [enter date and time]
**Decision:** ☒ GO WITH CONDITIONS

## CI evidence

- Latest run on `delivery/lead`: Green, according to the Actions result reviewed on November 10. Link: [paste your Actions run URL]
- Simulated run on `main`: Red at the test step. Two quote-creation tests returned 400 instead of 201 because the validation error reports an age minimum of 110.
- Workflow file: `.github/workflows/ci.yml`
- What the workflow actually checked: It checked out the code, set up Node 22, started a MongoDB service container, installed dependencies from the lock file, and ran the API test suite.

## What "GO" would mean

- Merge `delivery/lead` into `main` by squash merge only after `main` is green and the deployment owner has confirmed the customer-facing version.
- Delete the delivery branch after the merge.
- Tag the merge commit `phase-3`, as directed by the lab.

## What "NO-GO" would mean

- Hold the merge if `main` remains red or the deployed customer-facing version is unclear.
- Owner of that condition: Engineering/deployment owner for the `main` failure and deployment check.
- Re-evaluate at: Thursday morning check-in, or earlier if the owner confirms the cause and CI is green.

## My call

GO WITH CONDITIONS: my `delivery/lead` run is green, but the simulated run on `main` is red, so I will not merge onto a failing main branch. The red run failed in the tests and produced no build; because support reports customer impact, I’m asking the engineering/deployment owner to confirm what is actually deployed. I would proceed once `main` is green and the customer-facing version is understood.
