# Evergreen Quote: Vision Brief

## Product

**Name:** Evergreen Insurance Quote — full-stack launch  
**Delivery week:** Final capstone  
**Delivery Lead:** Samuel Ogunyemi [and partner, if paired]  
**Engineering team (represented by):** [Link to your Evergreen Quote repository]  
**GitHub Project board:** [Link to your project board]

## Who is the customer?

Our first customer is someone shopping for insurance for the first time, likely on a phone and comparing options. They want a quick, believable estimate without creating an account or making a phone call. The partner pilot team is another customer: it needs a way to request quote information through GraphQL. Operations needs a service that can be tested and run in a container and on the company’s Kubernetes platform. On Friday, our managers are also an audience: they need to see the customer journey clearly, without having watched the build.

## What pain does Evergreen Quote remove?

Today, the quote page can estimate a premium, but it forgets the customer’s quote when the page reloads. A separate service can store quotes, but the customer-facing app has never used it. Connecting the two means a shopper can move from the marketing page to an estimate, save the quote, and come back to find it still there. The estimate and the saved premium should agree, so the customer sees one dependable answer rather than two.

## What does “good” look like at the end of the week?

- A visitor can follow the landing-page link to the quote app.
- The app loads recent quotes from the API, and a newly saved quote remains after a reload.
- The displayed estimate and saved premium agree at the launch rates.
- The API runs as `evergreen-quote-api:2.0` and is demonstrated with three replicas on the local Kubernetes cluster.
- Both CI jobs are green on the reviewed change merged to `main`.

## What are we explicitly NOT doing this week?

- Adding authentication, accounts, or payments.
- Building a real-time or external rate engine.
- Adding product features that are not required for the launch.
- Making Friday’s required demo depend on AWS or the gated EKS exercise.

## How will we know if it worked?

- The saved quote is still visible after reloading the app.
- The API tests and client type-check/build pass, and both CI jobs are green on the merge commit.
- The five-minute showcase can demonstrate the journey from landing page to saved quote on the local cluster.

- ____________________________
find ~/Labfiles/WA3870-FinalProject/LabFiles/wa3870-cap-final-review-and-capstone-project-leaders \
  $$ -name '.env' -o -name '.env.example' -o -name '*.env.example' $$ -print
------
find .. -maxdepth 3 -name '*env*' -print

