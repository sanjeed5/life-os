# Command: /setup-private

## Objective
Create a private copy of LifeOS for personal use—completely separate from the public template.

## Workflow

1. **Check prerequisites**:
   - Verify `gh` CLI is installed and authenticated (`gh auth status`)
   - If not, guide user to install: `brew install gh && gh auth login`

2. **Get repo name**:
   - Ask user what they want to name their private repo (default: `life-os-private`)

3. **Remove public origin** (your private copy will be completely separate):
   ```bash
   git remote remove origin
   ```

4. **Create private repo and set as origin**:
   ```bash
   gh repo create <repo-name> --private --source=. --remote=origin --push
   ```

5. **Confirm success**:
   - Show the new private repo URL
   - Explain: "Your private LifeOS is now completely separate from the public template. No risk of accidentally pushing personal content."
   - Mention: "To get template updates in the future, check the public repo manually and copy over any changes you want."
   - Prompt: "Ready to personalize! Run `/onboard` to set up your profile."
