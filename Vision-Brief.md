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
I’m working on the Evergreen Quote API capstone. A POST request through my local Kubernetes Service succeeded, but for a home quote with age 45 and coverageAmount 200000, the API returned monthlyPremium 2400. The lab expects 2700 with the sponsor-approved home rate of 135.

Please investigate this mismatch using read-only checks first.

1. Check `src/premium.js` and report the configured home rate.
2. Check which image tag the Kubernetes Deployment uses.
3. Check whether the local Docker image `evergreen-quote-api:1.0` was built after the current source/configuration.
4. Explain why the cluster might return 2400 instead of 2700.
5. Recommend the smallest safe next steps.

Do not edit files or change code.
Do not change `.env`, `src/premium.js`, `Dockerfile`, Kubernetes manifests, or the image tag.
Do not delete any existing quotes or pods.
Do not run `kubectl apply`, restart deployments, rebuild/load images, or make other state-changing changes until you show me the exact commands and I approve them.
Do not run `npm audit fix`.
Do not print secrets or the contents of `.env`.

Report your findings and wait for my approval before making any changes.
