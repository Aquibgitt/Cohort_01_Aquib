# Student Workflow (Every Week)

## 1) Sync main
git checkout main
git pull origin main

## 2) Create a branch
git checkout -b week-XX

## 3) Commit + push
git add .
git commit -m "week XX: submit work"
git push -u origin week-XX

## 4) Open a PR (GitHub)
Base: main
Compare: week-XX
