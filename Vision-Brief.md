## Slide 1: Delivery goal & did we hit it? (45 seconds)

**Goal:** By Thursday’s end, the Evergreen Quote app loads and saves quotes through the API, shows estimates that match saved premiums, runs with its containerized API on the local Kubernetes cluster, and is merged to `main` through a reviewed pull request with both CI jobs green.

**Result: Yes.** We connected the landing page, quote app, and persistent API; verified the customer quote flow; demonstrated the containerized service on the local cluster; and merged the reviewed launch with both CI jobs green.

**Speaker note:** “A shopper can get a quote, save it, and find it again after reloading. We brought three previously separate pieces together and verified the result.”

## Slide 2: What shipped (60 seconds)

- The landing page directs visitors into the configured quote app.
- The app loads recent quotes from the API rather than bundled sample data.
- A saved quote persists after reload, and the estimate and saved premium agree at the launch rates.
- The API is packaged as `evergreen-quote-api:2.0` and demonstrated with three replicas and MongoDB on the local `kind` cluster.
- GraphQL is mounted, and a quote-creation mutation was demonstrated.
- Both CI jobs passed: API tests and client type-check/build.

**Evidence to show:**
- Screenshot of the wired client with database-backed quotes.
- Merged pull request: [insert PR URL].
- Green CI run on the merge commit: [insert Actions run URL].
- Optional EKS screenshot: the AWS console showed three API replicas and the MongoDB deployment ready. This confirms workload readiness at the time of capture; it does not prove the public quote request or cloud save-and-reload flow.

**Speaker note:** “The same client continued to work as the API moved from the development server to a container and then to Kubernetes. Friday’s demonstration uses the local cluster, so it does not depend on AWS.”

## Slide 4: Risks, incident, and response (60 seconds)

**Top risk tracked:** The customer app and API had never crossed a real network boundary. Their quote contracts could disagree, or the demo could appear fine until a field or saved value failed.

**How we reduced it:** The client type-check caught an ID-mapping defect at the seam. We applied the supplied fix, aligned the client rates to the API, and verified API-backed retrieval and persistence.

**Wednesday incident:** The incident was in the **shared demo environment**, not our local cluster. The supplied capture showed three restarting API pods, a healthy MongoDB pod, connections being attempted at `127.0.0.1`, and the deployment using `MONGO_URI` while the application expects `MONGODB_URI`. The platform team owns that environment, so we routed the evidence and recovery request to them instead of changing their cluster.

**Decision impact:** Our local `kind` cluster and CI were separate, verified evidence. Friday’s demo was planned on local `kind`, so the shared-environment incident did not gate our merge or change the demo plan.

**Speaker note:** “We named the environment that was affected, sent the issue to its owner, and based our launch decision on the environment we would actually use.”

## Slide 5: The program journey and what I take back (55 seconds)

**The journey:** A static page that made a promise → a typed React app that estimated instantly → an API and database that remembered quotes → one wired, containerized product demonstrated on Kubernetes and checked by CI.

**What I’ll take back to work:** I’ll make ownership, environment, and evidence explicit before acting—especially during incidents. I’ll route work to the team that owns it, state what I’ve verified, and give stakeholders a clear next update.

**What I’d do differently next time:** Confirm environment configuration and the demo path earlier, then reserve rehearsal time to verify the exact database and fallback—not just that the app opens.

**Closing line:** “The program taught us to build the parts. This launch taught me to bring them together, prove the customer path, and lead the work through to a clear decision.”
