# Stakeholder Status Update: Evergreen Quote

**To:** Priya Ramanathan, Project Sponsor  
**From:** Samuel Ogunyemi  
**Date:** November 17, 2026

## What shipped today

- Connected the quote app to the API, retired the bundled quote data, and verified that a saved quote persists after reload.
- Fixed the quote-ID mapping caught by the client type-check, aligned the client rates with the API, and mounted GraphQL. The GraphQL mutation returned a new quote with a monthly premium of $700.

## What changed (and why)

- I’ll update the landing-page hero and banner to lead with life coverage once we confirm the final wording. I’m not changing the quote form’s default from auto myself: that behavior lives in the client team’s application code, so I’ve routed the request to **[client owner/team]** for review against Friday’s launch. If it can’t be reviewed and verified in time, we’ll keep auto as the launch default.
- I recommend deferring renters until after launch. It crosses both the client’s coverage-type contract and the API’s database validation, which adds avoidable risk this late in the week.

## What’s next

- Complete and verify the approved life-first landing-page content; continue the container, local-cluster, and CI work.
- Friday’s demo will run on the local `evergreen` kind cluster. I’ll run `kubectl port-forward svc/evergreen-quote-api 3000:80` and show the wired client at `http://localhost:5173`, including a quote saved to and reloaded from the cluster database. The demo does not depend on a shared cloud environment.

## What I need from you

Please confirm the final life-first hero and banner wording by **10:30 Wednesday** so I can apply and verify it.
