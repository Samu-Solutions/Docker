# Program Showcase: Evergreen Quote

**Presenter:** Samuel Ogunyemi  
**Audience:** Managers, peers, and project sponsor  
**Target:** 5 minutes, followed by 3 minutes of questions

## Slide 1: Delivery goal & did we hit it?

- **Goal:** By Thursday’s end, the wired Evergreen Quote app saves quotes that survive a reload, shows an estimate that agrees with the saved premium, runs with its containerized API on the local Kubernetes cluster, and is merged to `main` through a reviewed pull request with both CI jobs green.
- **Hit?** ☒ Yes  ☐ Partially  ☐ No
- **Why:** The client and API were connected, the quote flow was verified, the API was containerized and demonstrated on local Kubernetes, and the launch was merged after review with both CI jobs green.

**Say:** “A shopper can get a quote, save it, and find it again after reloading. We brought three previously separate pieces together and verified the result.”

## Slide 2: What shipped

- **Customer journey:** The landing page links to the quote app; the app loads database-backed quotes, estimates a premium, and saves a quote that remains after reload.
- **Platform:** The API was packaged as `evergreen-quote-api:2.0` and demonstrated with three API replicas and MongoDB on the local `kind` cluster.
- **Partner path:** GraphQL was mounted and a quote-creation mutation was demonstrated.
- **Quality signal:** Both CI jobs passed—API tests and client type-check/build.
- **Merged PR:** [insert PR URL]
- **Green CI run:** [insert Actions run URL]
- **App evidence:** [insert screenshot or demo reference]

**Optional cloud evidence:** The EKS screenshots show three API replicas and one MongoDB deployment ready at the time of capture. They do not prove that a quote was saved through the public EKS endpoint. Friday’s demo ran on the local cluster.

**Say:** “The same client worked as the API moved from development to a container and then to Kubernetes. Our demo used the local cluster, so it didn’t depend on cloud access.”

## Slide 3: Two key decisions

### Decision 1: Align the client estimate to the API’s rates

- **Decision:** Keep the immediate client-side estimate, but align its rates to the API’s standardized rates: auto 90, home 135, and life 70. The API remains the source of truth for saved quotes.
- **Why it mattered:** Before alignment, the estimate and saved quote could show different premiums for the same customer. Aligning the values let the customer see one consistent answer without expanding launch scope.

### Decision 2: Protect launch scope while responding to the life-first request

- **Decision:** Approve the life-first landing-page content; route the request to change the quote form’s default to the client team for review; defer renters until after launch.
- **Why it mattered:** The landing-page wording is content the Delivery Lead can approve. The form default is application behavior owned by the client team, and renters crosses both client and API validation. Separating those decisions avoided slipping unreviewed code and added scope into launch week.

**Say:** “We didn’t treat every request as the same kind of change. We approved the content, routed the code request to its owner, and deferred the cross-stack feature to protect the launch.”

## Slide 4: Risks & injects

- **Top risk tracked:** The client and API had never crossed a real network boundary. Their contracts or premium values could disagree, making the demo look successful while the customer saw incorrect or missing information.
- **Mitigation:** The client type-check caught the ID-mapping defect; we applied the supplied fix, aligned the rates, and verified API-backed quote retrieval and persistence.
- **Inject #1 — launch pivot:** We separated the life-first landing content from the form-default code request, routed the form change to its owner, deferred renters, and documented the local demo plan.
- **Inject #2 — incident:** The incident capture was from the **shared demo environment**. Its API pods were restarting while MongoDB was healthy; the deployment showed `MONGO_URI` where the application expects `MONGODB_URI`. We routed it to the platform team rather than changing an environment we don’t own.
- **Go/no-go:** GO for the Friday demo on our verified local `kind` cluster, supported by [link to green CI run] and [local-cluster evidence]. The shared-cluster issue was tracked with its platform owner and did not by itself block our merge or local demo.

**Say:** “We kept the environments distinct: the shared demo cluster had an incident, while our own cluster and CI were the evidence for the Friday plan.”

## Slide 5: The journey in one slide, and what I take back to work

**The journey:**  
Static page → live, typed React app → API with a database → wired, containerized product running on an orchestrated platform.

**What I take back to work:**  
“I’ll make ownership, environment, and evidence explicit before acting—especially during an incident. I’ll route work to the right owner and give stakeholders a clear next update.”

**One thing I’d do differently next round:**  
Confirm environment configuration and the exact demo path earlier, and reserve rehearsal time to verify the database and fallback—not just that the app opens.

**Closing:**  
“The program taught us to build the parts. This launch taught me to connect them, prove the customer path, and lead the work through to a clear decision.”

## Q&A prep: likely questions

- **Why defer renters?** It was already deferred and would now touch both client-side and API validation. It wasn’t necessary for the agreed launch outcome, and taking it on late would increase testing and coordination risk.
- **Why not simply change the form default to life?** It was an application-code change owned by the client team, so it needed their review rather than an unreviewed launch-week edit.
- **Does green CI prove the whole customer journey?** No. CI checked the API tests and client type-check/build. We separately verified the integrated app against the local cluster.
- **Why didn’t the shared-cluster incident stop Friday’s demo?** It affected a different environment. Friday’s plan ran on our own local `kind` cluster, which we verified separately.
