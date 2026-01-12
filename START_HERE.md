# START HERE — How to Work on This Repo (Read Carefully)

This file explains EXACTLY how you will work on this repo every week.
Follow the steps in order.
Do not skip steps.
Do not work on `main`.

---

## WHAT THIS REPO IS

- This repo is your personal student repo.
- `main` is the final, reviewed version.
- All your work happens in branches.
- Every submission is done using a Pull Request (PR).

---

## RULES (IMPORTANT)

- ❌ Never push directly to `main`
- ✅ Always create a new branch for each week
- ✅ PR = submission
- ✅ PR merged = work accepted

If you break these rules, your work will not be reviewed.

---

## STEP 0: ONE-TIME SETUP (ONLY FIRST DAY)

Check Git is installed:
```bash
git --version
Set your name and email (do this once):
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
STEP 1: CLONE THE REPO (ONLY FIRST TIME)
Go to this GitHub repo → click Code → copy the URL.
Run:

git clone <REPO_URL>
cd <REPO_NAME>
Example:
git clone https://github.com/org-name/student-yourname.git
cd student-yourname
STEP 2: EVERY WEEK — SYNC MAIN (DO THIS FIRST)
Before starting any work:
git checkout main
git pull origin main
This makes sure your local repo is up to date.
STEP 3: CREATE A BRANCH FOR THE WEEK
Never work on main.
For Week 01:

git checkout -b week-01
For later weeks:
git checkout -b week-02
git checkout -b week-03
STEP 4: DO YOUR WORK
Put ALL your work inside the correct week folder.
Example structure:

week-01/
  exercises/
  notes/
  project/
You can add:
Python files
notebooks
notes
small projects
STEP 5: SAVE YOUR WORK (COMMIT)
After you finish your work:
git add .
git commit -m "week 01: submit work"
STEP 6: PUSH YOUR BRANCH TO GITHUB
git push -u origin week-01
This uploads your work to GitHub.
STEP 7: OPEN A PULL REQUEST (PR)
Go to the repo on GitHub
You will see Compare & pull request
Click it
Fill the PR:
Base branch: main
Compare branch: week-01
Title: Week 01 submission
Then click Create Pull Request.
This is your submission.

STEP 8: FIX REVIEW COMMENTS (IF ANY)
If the instructor asks for changes:
git add .
git commit -m "week 01: fixes after review"
git push
The PR updates automatically.
STEP 9: AFTER YOUR PR IS MERGED
Once your PR is merged:
git checkout main
git pull origin main
You are now ready for the next week.
SUMMARY (REMEMBER THIS)
Sync main
Create weekly branch
Do work
Commit
Push
Open PR
That’s it.

---

### What you should do now
1. Create `START_HERE.md` in `main`
2. Paste everything above
3. Commit and merge

After this, **your repo setup is complete** and students can start without confusion.

If you want next, I can:
- write a **1-minute verbal script** you say to students on Day 1  
- or create a **PR review checklist** for you  
- or simulate **student mistakes + fixes**

Just tell me.
