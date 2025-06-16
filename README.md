# AI Coding Assistant

## 📦 Project Structure

```markdown
/ai-docs
├── goals.md                # product goals and context
├── users.md                # personas, scenarios, and JTBD
├── tech-spec.yaml          # tech stack, dependencies, requirements
├── activities/             # user activities (high-level user journey)
│   └── activity-xxx.md     # each activity description
├── steps/                  # steps within activities
│   └── step-xxx.md         # each step description
├── stories/                # user stories tied to steps
│   └── story-xxx.md        # user story description
├── features/               # feature descriptions
│   └── feature-xxx.md      # each feature description
├── tasks/                  # decomposed tasks
│   └── task-xxx.md         # individual task description
├── components/             # UI/Logic/Data components
│   └── component-xxx.md    # component description
└── index.yaml              # links, execution order, and hierarchy
```

Each `.md` file uses **YAML frontmatter** so that AI and IDE can read metadata. Check each file template for more details.

---

## 🧠 How to Use This with AI in IDE (Cursor, Windsurf)

- Open `task-xxx.md` → AI reads frontmatter and knows:
  - tech stack
  - context of the activity/step/story/feature
  - input/output and requirements
- AI can access related files via links (used_in, related_to)
- This acts as documentation + context-driven code generation