Below is a ready-to-copy starter set for your GitHub Project board. Create each as a GitHub Issue, set its priority, then add it to the board. The issues follow the capstone’s assembly scope—use the provided kit pieces, and avoid adding unplanned features.

### 1. `[WIRE] Run all three parts and record the client/API gap` — P0

**Who it’s for:** The delivery team. **What they get:** A verified baseline and a shared understanding of the launch gap.

**Done criteria**
- [ ] Landing page, API, and client have each been started successfully.
- [ ] API health check succeeds and `/api/quotes` returns six seeded quotes.
- [ ] Record that the client shows bundled sample data rather than the API data.
- [ ] Record that a newly saved quote disappears after reload.

**Out of scope:** Wiring or fixing the client; that is a separate Tuesday issue.

### 2. `[WIRE] Connect the client to the API` — P0

**Who it’s for:** First-time shoppers. **What they get:** Recent quotes loaded from the quote service and saves persisted there.

**Done criteria**
- [ ] Copy the kit’s proxy, types, API module, context, and form files into their specified destinations.
- [ ] Client recent quotes show the API’s seeded records.
- [ ] Saving a quote and reloading shows that quote again.

**Out of scope:** Writing a new client or API implementation.

### 3. `[TYPES] Fix the client/API ID mapping` — P0

**Who it’s for:** Shoppers and the delivery team. **What they get:** Quote IDs mapped correctly across the API boundary.

**Done criteria**
- [ ] Run `npm run type-check` after installing the wiring files.
- [ ] Apply the kit’s specified `doc.id` → `doc._id` mapper fix.
- [ ] Run type-check again and confirm it passes.

**Out of scope:** Weakening or changing the API contract to hide the mismatch.

### 4. `[DATA] Retire the bundled quote stubs` — P0

**Who it’s for:** Customers and maintainers. **What they get:** One source of truth for recent quotes.

**Done criteria**
- [ ] Remove `client/src/sampleQuotes.ts` and `client/public/quotes.json` using `git rm`.
- [ ] Confirm the client loads its quote list from the API.
- [ ] Confirm a saved quote remains visible after reload.

**Out of scope:** Removing the API’s seed data or historical quotes.

### 5. `[CONFIG] Apply the launch values` — P0

**Who it’s for:** Shoppers arriving from the landing page. **What they get:** Correct launch branding, links, and consistent premiums.

**Done criteria**
- [ ] Set client rates to the API’s standardized rates: auto 90, home 135, life 70.
- [ ] Set `VITE_APP_TITLE` to the title supplied by the sponsor.
- [ ] Replace the landing-page banner placeholder with the sponsor’s wording.
- [ ] Point both landing-page quote links to `http://localhost:5173` for the lab demo.
- [ ] Verify estimate and saved premium agree for the same inputs.

**Out of scope:** Inventing title or banner copy; use the sponsor’s announcement.

### 6. `[GRAPHQL] Mount GraphQL and verify a mutation` — P1

**Who it’s for:** The partner pilot team. **What they get:** A GraphQL path to create and query quotes.

**Done criteria**
- [ ] Copy the provided GraphQL module and paste the two supplied lines at the API markers.
- [ ] Open the GraphQL explorer.
- [ ] Run the provided `createQuote` mutation and observe its ID and premium.
- [ ] Confirm the new quote appears in MongoDB.

**Out of scope:** Designing new GraphQL operations.

### 7. `[DOCKER] Build and run the API image` — P0

**Who it’s for:** Operations. **What they get:** The API packaged in a repeatable container image.

**Done criteria**
- [ ] Copy the provided Dockerfile and `.dockerignore` into `api/`.
- [ ] Build `evergreen-quote-api:2.0`.
- [ ] Run the container with the lab’s documented command.
- [ ] Verify the wired client can still reach the API.

**Out of scope:** Changing the API’s application code or publishing the image to a cloud registry.

### 8. `[K8S] Demonstrate the stack on local kind` — P0

**Who it’s for:** Operations and the showcase audience. **What they get:** A working cluster deployment of the launch service.

**Done criteria**
- [ ] Create the local `evergreen` kind cluster and apply the provided manifests in the documented order.
- [ ] Confirm three API pods and one MongoDB pod are running.
- [ ] Port-forward the API service to port 3000.
- [ ] Save a quote from the client and confirm it remains after reload in the cluster database.

**Out of scope:** Depending on AWS or the gated EKS exercise for the Friday demo.

### 9. `[CI] Enable and verify the two-job workflow` — P0

**Who it’s for:** The delivery team and maintainers. **What they get:** Automated checks for both sides of the launch.

**Done criteria**
- [ ] Copy the provided workflow to `.github/workflows/ci.yml`.
- [ ] Confirm the API test job passes.
- [ ] Confirm the client type-check/build job passes.
- [ ] Confirm both jobs are green on the PR and merged `main` commit.

**Out of scope:** Adding unrequested jobs or changing the workflow design.

### 10. `[BUILD] Build and preview the production client` — P0

**Who it’s for:** The launch audience. **What they get:** A verified production build connected to the API.

**Done criteria**
- [ ] Run `npm run build` in `client/`.
- [ ] Run `npm run preview`.
- [ ] Confirm recent quotes load from the API in the preview build.
- [ ] Confirm saving a quote and reloading works.

**Out of scope:** Committing generated `dist/` output.

### 11. `[REVIEW] Review and merge the launch PR` — P0

**Who it’s for:** The engineering organization. **What they get:** A reviewed, tested launch on `main`.

**Done criteria**
- [ ] Open a PR from `delivery/lead` to `main`.
- [ ] Review the complete diff and leave at least one question-style inline comment.
- [ ] Confirm both CI jobs are green on the PR.
- [ ] Squash and merge, then delete the branch.
- [ ] Pull `main` and smoke-test the app.

**Out of scope:** Merging with unresolved red CI checks.

### 12. `[SHOWCASE] Prepare and rehearse the five-minute showcase` — P0

**Who it’s for:** Managers, peers, and the sponsor. **What they get:** A clear demonstration of the program’s end-to-end outcome.

**Done criteria**
- [ ] Prepare five slides or one concise page using the template.
- [ ] Include the delivery goal, shipped evidence, decisions, risks/injects, and program journey.
- [ ] Rehearse aloud and finish within five minutes.
- [ ] Document live-demo setup and a screenshot fallback.

**Out of scope:** Making the presentation depend on the gated cloud exercise.

### Add a board note

Your initial observed risk can be summarized as:

> **Risk:** The client currently displays bundled sample quotes and does not persist saves through the API. Until the wiring is complete, the customer experience cannot demonstrate a quote that survives reload.  
> **Mitigation:** Complete the provided wiring steps, run the type-check and API tests, and verify save-and-reload against the API before the demo.

You can paste each issue description into GitHub as written. Move issues through **To Do → In Progress → Done** as work proceeds.

This content was generated by LibertyGPT and should be reviewed for accuracy.
