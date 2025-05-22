How to Safely Update and Maintain Your Custom Eriteach AI lab Fork
This guide explains what has been done to customize your fork of Open WebUI, and how to safely update your fork in the future while keeping your custom branding and changes.


What Has Been Done
All visible references to "Open WebUI" have been replaced with "Eriteach AI lab" in the UI, translation files, and documentation.
Custom favicon and logo have been added.
Docker image and container names have been rebranded to eriteach-ai-lab.
Telemetry/tracking has been removed (if present).
All changes are committed to your fork at https://github.com/thugney/open-webui.git.
Custom Docker images are tagged and pushed to ghcr.io/thugney/eriteach-ai-lab (use :main or :cuda as needed).


How to Update Your Custom Fork in the Future (Step-by-Step)
Make Sure Your Remotes Are Set Up

origin should point to your fork: https://github.com/thugney/open-webui.git
upstream should point to the original: https://github.com/open-webui/open-webui.git
Check with:
git remote -v

Fetch the Latest Changes from Upstream
git fetch upstream
Create a New Branch for the Update
git checkout main
git pull origin main
git checkout -b update-from-upstream
git merge upstream/main
If there are conflicts, Git will pause and ask you to resolve them.
Open the conflicted files, and make sure to keep your custom branding and changes.
After resolving, mark as resolved:

git add .
git commit

Test Your Project

Build and run your project locally or with Docker.
Make sure your branding and customizations are still present and nothing is broken.
Push the Update Branch to Your Fork

git push origin update-from-upstream

Merge the Update Branch

On GitHub, create a Pull Request from update-from-upstream into your main branch.
Review the changes and merge when ready.
Rebuild and Deploy Your Custom Docker Image

For a standard image:
docker build -t ghcr.io/thugney/eriteach-ai-lab:main .
docker push ghcr.io/thugney/eriteach-ai-lab:main

Always use a new branch for updates.
Never merge upstream changes directly into your main branch without review.
Test thoroughly after every update.
Keep a backup of your main branch before merging major updates.
Make sure your GitHub PAT has write:packages and read:packages scopes for pushing to ghcr.io.
