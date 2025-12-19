# Command: /onboard

## Objective
Set up `user.md` with minimal friction—auto-detect what you can, ask permission for the rest.

## Workflow

### 1. Welcome & ask permission (one ask)
Greet the user, then ask permission for everything upfront:

> "To set up your profile, I can auto-detect some info to save you time:
> - **From your system**: name, email, timezone
> - **From connected services** (calendar, email, etc.): schedule and context
> - **From web search**: public info like your work, projects, or interests (if you'd like)
>
> Can I go ahead and check these?"

If yes → proceed to step 2
If no → skip to step 3 (manual interview for everything)

### 2. Auto-detect (only if permitted)
**From shell:**
- **Name**: `git config user.name` or `id -F` (system full name)
- **Email**: `git config user.email`
- **Timezone**: `date +%Z` and `readlink /etc/localtime | sed 's|.*/zoneinfo/||'`

**From MCP (if integrations are available):**
- Check available MCP tools and use what's relevant:
  - **google-workspace**: Check for calendar patterns, email context, drive documents
  - **Calendar** → work patterns, meeting load, time blocks
  - **Email** → context, deadlines, communication style
  - **Docs/Drive** → current projects, work focus areas
- Note insights for preferences, but don't overwhelm

**From web search (if permitted and available):**
- After gathering name and email, perform a web search to find:
  - Professional background (LinkedIn, company pages, GitHub, portfolio)
  - Current projects or work (blog posts, publications, repos)
  - Public interests or expertise areas
  - Speaking engagements, articles, or contributions
- **Privacy first**: Only use publicly available information
- **Be selective**: Focus on recent, relevant context that helps personalization
- **Format**: Search using user's name and email domain to find professional profiles
- **Limitations**: If search returns nothing or privacy concerns arise, skip gracefully

### 3. Interview (only what can't be auto-detected)
Ask these in one or two messages—keep it conversational, not interrogative:

**Core (required):**
- **Role**: "What's your current role? (e.g., Engineer at Acme, Freelance designer, Student)"
- **Priorities**: "What are your top 2-3 priorities or projects right now?"
- **Style**: "Do you prefer things concise or detailed?"

**Context (helps personalization):**
- **Interests**: "Any hobbies or interests outside work? (helps me suggest breaks and balance)"
- **Energy**: "When do you do your best work? Any times to protect or avoid? (e.g., mornings for deep work, no meetings before 10am)"

### 4. Update `user.md`
- Fill in all sections using auto-detected + answered info
- Keep the existing Markdown structure

### 5. Confirm & launch
- Show the completed user.md content
- If good, suggest: "Ready! Run `/start` to begin your first day."

## Notes
- One permission ask covers shell, integrations, AND web search—don't ask multiple times
- If user says no, fall back to manual questions gracefully
- If no integrations are connected, just use shell detection + manual questions
- Web search is optional and should respect privacy—only use public info
- If search yields sensitive or unexpected results, ask before including in profile
