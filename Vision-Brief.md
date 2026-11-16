# Delivery Goal: Evergreen Quote

## Goal

> By Thursday’s end, the Evergreen Quote app will load and save quotes through the API, show estimates that match saved premiums, run with its containerized API on the local Kubernetes cluster, and be merged to `main` through a reviewed pull request with both CI jobs green.

## “Done” looks like

- The quote page loads recent quotes from the API, and a saved quote survives a reload.
- The on-screen estimate and saved premium agree at the launch rates.
- The API tests pass; the client type-check and production build pass; both CI jobs are green on the merge commit.
- The containerized API serves the wired app, and the local cluster demo shows three API pods behind one Service.
- The landing page has the sponsor-approved launch banner and links to the app.
- A reviewed pull request is merged to `main`, and the working branch is deleted.
- The completed `delivery-leadership-package/` is committed to the repository.

## Out of scope (this week)

- Authentication, customer accounts, or payments.
- Building a real-time or external rate engine.
- Making the required Friday demo depend on AWS or the gated EKS exercise.
