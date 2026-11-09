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

# Risk Register

| # | Risk | Owner | Likelihood (L/M/H) | Impact (L/M/H) | Mitigation | Trigger to escalate |
|---|---|---|---|---|---|---|
| R1 | The API could say a quote was created successfully even though the premium is wrong. We saw this earlier: the response looked fine, but the premium was `$0.35` instead of `$400`. | Samuel (delivery lead); Engineering team for route issues | M | H | Run the tests after changes to the routes or premium settings. Check the premium in a sample quote before calling the API ready. | A premium test fails, or a sample quote has a premium that does not match the agreed rates. |
| R2 | A quote created before the fix could still be sitting in the database with the wrong premium. Fixing the route does not automatically fix data already saved. | Samuel (delivery lead); Engineering team for data questions | M | M | Keep track of test data created before the fix. Reset to the supplied seed data before the cluster demo, as the lab instructs. | An old or incorrect quote appears in a demo or someone treats it as valid customer data. |
| R3 | The service name or premium rates could be set incorrectly or differ from what the sponsor approved. | Samuel (delivery lead); Sponsor for confirming decisions | M | H | Confirm the sponsor’s decisions, update only the named settings, restart the service after changing `.env`, and check a sample response. | The sponsor’s decision is unclear, or the API response does not match the approved name or rates. |
| R4 | GraphQL might not be connected properly, or it could return different results from REST. | Samuel (delivery lead); Engineering team for GraphQL issues | M | M | Check the explorer, run the quote list and lookup queries, try the create mutation, and confirm the created quote also appears through REST. | The explorer is unavailable, a required query or mutation fails, or the REST and GraphQL results disagree. |
| R5 | We do not yet know whether CI is green. A local test pass alone does not confirm that the GitHub workflow will pass. | Samuel (delivery lead); Engineering/CI owner if help is needed | M | H | Enable the provided workflow, check the Actions run and read its logs. Keep a green CI run as a requirement for merging. | CI is red, has not started, or is still incomplete when it is time to merge. |
| R6 | The instructor’s inject may change what needs attention and take time away from planned work. | Samuel (delivery lead) | M | M | Reorder the board after the inject, note what moved and why, and tell the sponsor what decision or help is needed. | The inject blocks a priority task or puts the delivery goal at risk. |
| R7 | Working solo means one person has to assemble, check, document, and communicate the work. There may not be enough time for every task. | Samuel (delivery lead); Sponsor for priority or scope decisions | M | M | Focus first on required work, leave optional challenges until the essentials are done, and raise schedule or scope concerns early. | A required milestone is likely to slip, or completing it would require dropping another required item. |

## How I’ll use this register

I’ll check these risks as I plan each day and after the instructor’s injects. If something changes, I’ll update the register and raise blockers or decisions early rather than waiting until the final review. Since I’m working solo, I’ll keep the focus on required work and ask the sponsor for help with priority decisions when needed.
