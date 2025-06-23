# Instructions for Vibe Coding with AI Coding Assistant

These instructions guide you through using the AI Coding Assistant project structure for "vibe coding" — an intuitive, context-driven, AI-supported workflow to create clear documentation that enables the AI to build a project by executing a well-defined list of tasks and components. The goal is to produce a single source of truth that allows the user to control and navigate the development process, with the AI generating and implementing tasks and components one by one. The workflow uses User Story Mapping to define user journeys and Feature Mapping to create executable acceptance criteria, ensuring clarity for AI-driven development.

## 🚀 Getting Started

### 1. Understand the Project Structure

The `/ai-docs` directory provides a structured framework for documentation, ensuring the AI has the context to generate and implement tasks and components. Familiarize yourself with the structure:

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

Each file uses **YAML frontmatter** (e.g., `id`, `status`, `tech_context`) to provide metadata for AI-driven coding and navigation.

### 2. Set Up Your IDE

- **IDE Compatibility**: Use an IDE like Cursor or Windsurf with AI integration and markdown/YAML parsing.
- **File Access**: Ensure the `/ai-docs` directory is accessible in your IDE.
- **AI Configuration**: Enable plugins/extensions for markdown and YAML parsing to allow the AI to read metadata and linked files.

### 3. Vibe Coding Workflow

The workflow focuses on creating clear, actionable documentation to guide the AI in building the project through a sequential list of tasks and components, with user control and navigation. It leverages User Story Mapping for user journeys and Feature Mapping for executable criteria, as inspired by John Ferguson Smart’s Feature Mapping.

#### Step 1: Define Goals and Context

- **Open** `goals.md`: Capture the project’s purpose (e.g., "Simplify personal finance management"), success metrics (e.g., task completion rate), and target audience.
- **Review** `users.md`: Define user personas (e.g., "Busy Professional") and JTBD (e.g., "When I’m on the go, I want to log expenses, so I can track my budget").
- **Check** `tech-spec.yaml`: Specify the tech stack (e.g., Dart, Flutter) and constraints (e.g., mobile-first, no local file I/O).
- **Purpose**: These files provide the AI with the project’s context, ensuring all subsequent documentation aligns with user needs and technical requirements.

#### Step 2: Generate Activities, Steps, and User Stories (User Story Mapping)

- **Goal**: Create a user story map to define high-level user journeys, broken into activities, steps, and stories, providing the foundation for task and component creation.
- **Use AI Prompt Template**:
  - Copy the User Story Mapping prompt (below) into your IDE.
  - Customize the context with details from `goals.md` and `users.md`.
  - Execute to generate:
    - Activities (`activities/*.md`): High-level user journeys (e.g., "Manage Expenses").
    - Steps (`steps/*.md`): Specific actions (e.g., "Add Expense").
    - User Stories (`stories/*.md`): User needs in the format "As a \[user\], I want to \[do something\], so that \[value\]."
    - Updated `index.yaml` snippet for hierarchy and relationships.
- **Review and Save**:
  - Ensure YAML frontmatter includes `id`, `status: draft`, and links (e.g., `related_goals`, `activity`).
  - Save files in `activities/`, `steps/`, and `stories/`.
  - Update `index.yaml` to reflect the new files.
- **Outcome**: A user story map that outlines user journeys, ready for refinement into features and tasks.

**User Story Mapping Prompt Template**:

```
You are an AI Coding Assistant tasked with generating User Activities, User Steps, and User Stories for an AI-oriented project management and coding environment. Using `goals.md` and `users.md`, create a user story map following User Story Mapping principles. Follow the project structure in `README.md` and templates in `activity-xxx.md`, `step-xxx.md`, and `story-xxx.md`. Ensure YAML frontmatter includes `id`, `status`, and relevant links.

**Input Files**:
- `goals.md`: Primary goal, success metrics, target audience.
- `users.md`: User personas, scenarios, JTBD.
- `tech-spec.yaml`: Tech stack and constraints.

**Instructions**:
1. Generate a full list of User Activities (`activities/*.md`):
   - Represent high-level user journeys tied to goals and personas.
   - Include purpose, description, and YAML frontmatter (`id: activity-<unique-id>`, `status: draft`, `related_goals: [goals.md]`).
2. Generate Steps per User Activity (`steps/*.md`):
   - Break down each activity into specific actions.
   - Include YAML frontmatter (`id: step-<unique-id>`, `status: draft`, `activity: activity-<id>`).
3. Generate User Stories per Step (`stories/*.md`):
   - Use format: "As a [user], I want to [do something], so that [value]."
   - Include 2-3 acceptance criteria, constraints, and YAML frontmatter (`id: story-<unique-id>`, `status: draft`, `actor: <persona>`, `tech_context: ../tech-spec.yaml`).
4. Update `index.yaml`:
   - Add activities, steps, and stories to `activities` section.
   - Update `execution_order` and `status`.

**Constraints**:
- Align with `tech-spec.yaml`.
- Use unique IDs (e.g., `activity-001`).
- Keep descriptions user-focused and concise.

**Output**:
- Markdown files for activities, steps, and stories.
- Updated `index.yaml` snippet.
- Wrap each file in `<xaiArtifact>` with unique `artifact_id`, `title`, and `contentType="text/markdown"`.

**Example Context**:
- Goal: Simplify personal finance management.
- Persona: Busy Professional, JTBD: "When I’m on the go, I want to quickly log expenses, so I can track my budget."
```

#### Step 3: Refine Stories into Features (Feature Mapping)

- **Goal**: Transform user stories into detailed, executable features with clear acceptance criteria, enabling the AI to create tasks and components. Feature Mapping breaks stories into examples, steps, rules, and consequences for clarity and automation.
- **Use AI Prompt Template**:
  - Copy the Feature Mapping prompt (below) into your IDE.
  - Specify a user story (e.g., `stories/story-001.md`).
  - Execute to generate:
    - Features (`features/*.md`): Detailed functionality with executable acceptance criteria, including example tables (Example, Steps, Rule, Consequence).
    - Question tasks (`tasks/*.md`): For uncertainties identified during mapping.
    - Updated `index.yaml` snippet.
- **Review and Save**:
  - Verify feature files include testable criteria and link to stories, tasks, and components.
  - Save in `features/` and update `index.yaml`.
- **Outcome**: A clear feature map that defines functionality and acceptance criteria, ready for task decomposition.

**Feature Mapping Prompt Template**:

```
You are an AI Coding Assistant tasked with performing Feature Mapping to refine user stories into executable acceptance criteria. Using `stories/story-<id>.md`, apply Feature Mapping principles (per https://johnfergusonsmart.com/feature-mapping-a-simpler-path-from-stories-to-executable-acceptance-criteria/) to generate a feature file. Follow the project structure and `feature-xxx.md` template.

**Input Files**:
- `stories/story-<id>.md`: User story, acceptance criteria, actor, goal, constraints.
- `users.md`: User personas, JTBD.
- `goals.md`: Primary goal, success metrics.
- `tech-spec.yaml`: Tech stack, constraints.

**Instructions**:
1. Analyze the User Story:
   - Extract actor, goal, and constraints.
2. Perform Feature Mapping:
   - Break into sequential steps (user actions, system responses).
   - Generate 3-5 examples (happy paths, edge cases, negative scenarios).
   - Define business rules (e.g., "Amount > 0").
   - Specify consequences (e.g., "Expense saved").
   - Identify questions/uncertainties as tasks (e.g., "What currencies are supported?").
3. Generate Feature File (`features/feature-<unique-id>.md`):
   - Use `feature-xxx.md` template.
   - Include YAML frontmatter (`id: feature-<unique-id>`, `status: draft`, `priority: medium`, `related_stories: [story-<id>]`, `tech_context: ../tech-spec.yaml`).
   - Structure: Purpose, Description, Input Data, Output Data, Acceptance Criteria (with example table), Dependencies.
4. Generate Question Tasks (`tasks/task-<unique-id>.md`):
   - For each question, create a task with YAML frontmatter (`id: task-<unique-id>`, `status: draft`, `type: question`).
5. Update `index.yaml`:
   - Add feature and tasks to `activities` and `feature_dependencies`.
   - Update `execution_order` and `status`.

**Constraints**:
- Align with `tech-spec.yaml`.
- Use unique IDs.
- Ensure acceptance criteria are testable.
- Link files via YAML frontmatter.

**Output**:
- `features/feature-<id>.md` with example table (Example, Steps, Rule, Consequence).
- `tasks/task-<id>.md` for questions.
- Updated `index.yaml` snippet.
- Wrap each file in `<xaiArtifact>` with unique `artifact_id`, `title`, and `contentType="text/markdown"`.

**Example Context**:
- Story: "As a Busy Professional, I want to log expenses, so I can track my budget."
- Criteria: Expense saved, error for invalid amounts.
- Constraints: Positive amounts, authorized users.
```
#### Step 4: Define Architecture
- **Goal**: Create an architecture.md file detailing the project’s full architecture, including file structure, component roles, state management, and service connections.
**Process:**
- Use the AI with the prompt below, filling in your project details (e.g., "mobile app for task management").
- The AI will generate architecture.md based on goals.md, users.md, tech-spec.yaml, and features/*.md.
- **Prompt:**

  ```
  I'm building a [mobile app / web service] for [description of your product - the more detailed the better]. Use [Language or framework] for frontend, [Supabase | Firebase] for DB + auth.
  Give me an architecture.md file with the full architecture:
  - File + folder structure
  - What each part does
  - Where state lives, how services connect
  Additional context: Project goals are in goals.md, user personas and scenarios are in users.md, tech stack is in tech-spec.yaml, and features are in features/*.md. Output in markdown format with clear sections.
  ```

#### Step 5: Implement Tasks and Components with AI

- **Goal**: Have the AI execute tasks and build components one by one, guided by the documentation.
- **Process**:
  - **Select Task**: Open a task file (e.g., `tasks/task-001.md`) and review its description, completion criteria, and output (e.g., `StatelessWidget`).
  - **Generate Code**: Prompt the AI:
    - Prompt: "Generate a \[output, e.g., Dart StatelessWidget\] for `task-<id>` based on `feature-<id>`, `component-<id>`, and `tech-spec.yaml`."
  - **Build Component**: Open a component file (e.g., `components/component-001.md`) and prompt:
    - Prompt: "Generate a \[language, e.g., Dart\] \[type, e.g., UI\] component for `component-<id>` with specified inputs and outputs."
  - **Integrate**: Ensure components are linked as per `used_in` and `depends_on` in YAML frontmatter.
- **Outcome**: A growing codebase with AI-generated implementations, traceable to tasks and features.

#### Step 6: Navigate and Control the Process

- **Use** `index.yaml`:
  - **Navigation**: Review `activities`, `execution_order`, and `*_dependencies` to track progress and dependencies.
  - **Control**: Prioritize tasks by updating `execution_order` or `status` (e.g., `draft` to `in-progress`).
  - **AI Assistance**: Prompt the AI to suggest the next task:
    - Prompt: "Based on `index.yaml`, recommend the next task to implement and generate its code."
- **Monitor Status**:
  - Update `status` in tasks, features, and components as you progress (e.g., `in-progress`, `done`).
  - Use `index.yaml`’s `status` section to track completion.

#### Step 7: Validate and Iterate

- **Test**: Run code in your IDE and validate against acceptance criteria in `features/*.md`.
- **Refactor**: Prompt the AI to refine code:
  - Prompt: "Refactor `task-<id>` code to meet `tech-spec.yaml` constraints."
- **Update Documentation**: Reflect changes in `tasks/*.md`, `components/*.md`, and `index.yaml`.

### 4. Example Workflow

**Scenario**: Build a feature for logging expenses in a budgeting app.

1. **Define Context**: Update `goals.md` (Goal: Simplify personal finance management), `users.md` (Persona: Busy Professional, JTBD: Log expenses on the go), and `tech-spec.yaml` (Dart, Flutter).
2. **User Story Mapping**:
   - Run the User Story Mapping prompt to generate `activity-add-expense.md`, `step-add-expense.md`, and `story-add-expense.md` (e.g., "As a Busy Professional, I want to log expenses, so I can track my budget").
   - Update `index.yaml`.
3. **Feature Mapping**:
   - Run the Feature Mapping prompt for `story-add-expense.md` to generate `feature-add-expense.md` with:
     - Example table: (Valid expense, Enter amount, Amount &gt; 0, Expense saved).
     - Question task: `task-clarify-currencies.md` (e.g., "指標: "What currencies are supported?").
   - Update `index.yaml`.
4. **Create Tasks and Components**:
   - Generate `task-add-expense-ui.md` (output: StatelessWidget) and `component-expense-form.md` (type: UI, language: Dart).
   - Update `index.yaml`.
5. **Implement**:
   - Prompt: "Generate a Dart StatelessWidget for `task-add-expense-ui` based on `feature-add-expense` and `tech-spec.yaml`."
   - Prompt: "Generate a Dart UI component for `component-expense-form`."
6. **Validate**: Test against feature criteria.
7. **Navigate**: Use `index.yaml` to select the next task.
8. **Update**: Mark tasks as `done` in `index.yaml`.

### 5. Tips for Vibe Coding

- **Clear Prompts**: Reference specific files and metadata in prompts.
- **Validate Outputs**: Check AI-generated files and code for accuracy.
- **Maintain Links**: Ensure YAML frontmatter links related files.
- **Control Progress**: Use `index.yaml` to prioritize and track tasks.
- **Iterate Freely**: Experiment with AI-generated code, but validate against criteria.

### 6. Troubleshooting

- **Vague AI Outputs**: Use precise prompts with file references.
- **Incomplete Features**: Refine Feature Mapping prompts for clearer criteria.
- **Dependency Issues**: Check `index.yaml` for missing links.
- **Code Fails Tests**: Revisit feature criteria and adjust prompts.
- **Navigation Confusion**: Use `index.yaml` to trace relationships.

### 7. Best Practices

- **Granular Tasks**: Keep tasks small and specific for AI execution.
- **Testable Criteria**: Ensure feature acceptance criteria are clear and automatable.
- **Regular Updates**: Maintain `index.yaml` and status fields.
- **Collaborate with AI**: Use AI for generation and refactoring, but verify outputs.

This workflow ensures clear documentation drives AI implementation, with a structured task and component list for user-controlled development.