# oh-damn-clients

## Copy standards

Any marketing/outbound copy drafted or finalized in this repo — cold emails, LinkedIn messages, website copy, ad copy, etc. — must be run through the `humanizer` skill (`/humanizer`) before it is presented as done. Do this automatically as the last step; don't wait to be asked.

Reference the relevant client's `Assets/Brand Voice/` guide (e.g. `Assets/Brand Voice/tone-of-voice-guide.md` for CashLab) when drafting, then humanize before delivering.

If the `humanizer` skill isn't installed/available in the session, install it before using it — don't skip humanizing and don't ask the user to install it themselves:

```bash
mkdir -p ~/.agents/skills/humanizer
curl -sL https://raw.githubusercontent.com/blader/humanizer/main/SKILL.md -o ~/.agents/skills/humanizer/SKILL.md
ln -s ../../.agents/skills/humanizer ~/.claude/skills/humanizer
```

Then proceed with `/humanizer` as normal.
