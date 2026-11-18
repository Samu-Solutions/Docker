# Go / No-Go: Launch Decision

**Date / time:** November 18, 2026 / [time]
**Decision:** ☒ GO WITH CONDITIONS

## CI evidence

- Latest run on `delivery/lead` (both jobs): [green / red] · link: [paste Actions run URL]
- Workflow file: `.github/workflows/ci.yml`
- What the workflow checked: API tests using a MongoDB service; client type-check and production build.

## What "GO" means

- Proceed with the reviewed PR from `delivery/lead` to `main` only when both CI jobs are green.
- Confirm the local `evergreen` kind cluster is healthy and the demo quote can be saved and reloaded there.
- Keep Friday’s demo on the local cluster; it does not depend on the shared demo environment.

## What would stop or change this call

- Hold the merge if either CI job is red, or if our local cluster cannot serve and persist a demo quote.
- The platform team owns the shared demo-cluster incident. Track its recovery separately; it is not a reason to patch that cluster ourselves or to claim it is healthy.
- Reassess if the incident reveals a shared dependency that Friday’s local demo actually needs.

## My call

I’m calling GO WITH CONDITIONS for Friday’s demo on our local `evergreen` kind cluster, subject to confirming that our own cluster and both CI jobs are green. The incident capture is from the separate shared demo cluster: its API pods are restarting after a likely environment-variable mismatch, while its MongoDB pod is healthy. The platform team owns that environment and the recovery; I will track their update, but this incident does not gate our merge unless new evidence shows Friday’s local demo depends on it.
