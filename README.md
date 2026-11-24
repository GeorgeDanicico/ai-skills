# ai-skills

Reusable [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills).

## Skills

### `interactive-topic-tutor`

Teaches one short topic (20 minutes max) from a topics file you provide: a clear explanation, a concrete worked example, a common pitfall, then 2–3 questions to check your understanding. At the end it offers to save a Markdown wrap-up of the session, and (if your file uses `- [ ]` checkboxes) to tick off the topic.

#### Install

1. Copy the folder into your personal skills directory (or a project's `.claude/skills/`):

   ```bash
   cp -R interactive-topic-tutor ~/.claude/skills/
   ```

2. Open `~/.claude/skills/interactive-topic-tutor/SKILL.md` and replace the placeholders:

   | Placeholder | Meaning | Example |
   |---|---|---|
   | `{{TOPICS_FILE}}` | Absolute path to your topics Markdown file | `/Users/me/Learning/kubernetes-topics.md` |
   | `{{NOTES_DIR}}` | Where wrap-up files are saved | `/Users/me/Learning/session-notes` |
   | `{{SUBJECT}}` | Short subject name | `Kubernetes` |

   Placeholders you leave unfilled have a fallback: the skill will ask for the topics file, save notes next to it in `session-notes/`, and infer the subject from the file title.

3. Optionally rename the folder and the `name:` field (e.g. `kubernetes-tutor`) if you want several tutors for different files.

#### Use

```
/interactive-topic-tutor               # suggests 3 unlocked topics (prerequisites done)
/interactive-topic-tutor topic 42      # teaches a specific topic
teach me the next topic                # natural language works too
```

#### Topics file format

Anything readable works, but this format gets the most out of the skill:

```markdown
# My subject

## 01. Area name
- [ ] 001. Topic title — the exact scope of the lesson.
- [x] 002. Already-learned topic — its scope.
```
