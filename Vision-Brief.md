cd ~/evergreen-quote-launch
----
mkdir -p .github/workflows
---
KIT="$HOME/LabFiles/WA3870-FinalProject/LabFiles/wa3870-cap-final-review-and-capstone-project-leaders"
---
cp "$KIT/workflows/ci.yml" .github/workflows/ci.yml
----
git add .github
----
git commit -m "Enable CI"
----
git push
----
