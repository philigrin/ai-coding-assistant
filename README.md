# Project Structure Template

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

Each `.md` file uses **YAML frontmatter** so that AI and IDE can read metadata.

---

### 🪜 Steps to Build `/ai-docs`

1. **Create `goals.md`** — describe the 1–3 key business/user goals the app solves
2. **Create `users.md`** — document user personas, scenarios of use, and JTBD
3. **Create `tech-spec.yaml`** — specify tech stack, platforms, languages, dependencies (e.g., Flutter + Supabase)
4. **User Story Mapping**:
    - Define high-level **Activities** (e.g., "Manage Expenses") in `activity-xxx.md`
    - Break each Activity into **Steps** (e.g., "Add Expense") in `step-xxx.md`
    - Map each Step to one or more **User Stories** in `story-xxx.md`
5. **Feature Mapping**:
    - Each User Story maps to one or more Features
    - Create `feature-xxx.md` for each feature
6. **Task Breakdown**:
    - Break down each feature into tasks in `task-xxx.md`
7. **Component Breakdown**:
    - UI / logic / data components described in `component-xxx.md`
8. **Link everything in `index.yaml`**:
    - Reference activity → step → story → feature → task → component
    - Include priorities, status, and execution order

---

### `goals.md` – 1–3 key business/user goals the app solves

```markdown
---
title: Product Goals and Scope
version: 1.0
author: YOUR_NAME
---

## 🎯 Primary Product Goal

<!-- Describe the main problem this app is solving -->

## 📊 Key Success Metrics

- <!-- e.g., Daily Active Users, Retention Rate, Task Completion % -->

## ❓ Problem Being Solved

<!-- What frustration or inefficiency are you addressing? -->

## 🧑‍💻 Target Audience

<!-- Describe key user personas: who are they, what are their needs? -->
```

## `users.md` – user personas, scenarios of use, and JTBD

```markdown
---
title: Users and Scenarios
version: 1.0
author: YOUR_NAME
---

## 👤 User Personas

- <!-- Persona 1: role, background, needs, pain points -->
- <!-- Persona 2: role, background, needs, pain points -->

## 🧬 Scenarios of Use

- <!-- Everyday situations where the app is useful → context, goal, device -->
- <!-- Include motivations and potential blockers -->

## 💼 Jobs-To-Be-Done (JTBD)

- When [situation], I want to [motivation], so I can [expected outcome]
- When [situation], I want to [motivation], so I can [expected outcome]
```

## `activity-xxx.md` – high-level **Activities**

```markdown
---
id: activity-xxx
title: Activity Name
status: draft  # draft | planned | in-progress | done
related_goals: [goals.md]
---

## 🎯 Purpose

<!-- High-level user activity (e.g., "Manage Expenses") and its role in achieving goals -->

## 📋 Description

<!-- Brief explanation of what this activity entails and its scope -->

## 🔗 Related Steps

- step-xxx
```

## `step-xxx.md` – step description

```markdown
---
id: step-xxx
title: Step Name
status: draft  # draft | planned | in-progress | done
activity: activity-xxx
---

## 🎯 Purpose

<!-- Specific step within an activity (e.g., "Add Expense") -->

## 📋 Description

<!-- What the user does in this step and why -->

## 🔗 Related Stories

- story-xxx
```

## `tech-spec.yaml` – separate YAML file with technical context

```yaml
project:
  name: # e.g., "my_cool_app"
  type: # "mobile" or "web"
  platform: # e.g., "flutter"
  architecture: # e.g., "clean_architecture"

stack:
  frontend: # e.g., "flutter"
  state_management: # e.g., "riverpod"
  data_storage: # e.g., "supabase"
  backend: # e.g., "supabase"
  auth: # e.g., "supabase_auth"
  local_storage: # e.g., "hive"
  analytics: # e.g., "firebase"
  CI_CD: # e.g., "github_actions"

design:
  system: # e.g., "material_3"
  components_library: # e.g., "flutter_ui_kit"

conventions:
  file_naming: # e.g., "snake_case"
  widget_type: # e.g., "prefer_stateless"
  folder_structure: # e.g., "feature_based"

dependencies:
  packages:
    - # e.g., "flutter_riverpod"
    - # e.g., "freezed"
    - # e.g., "json_serializable"
    - # e.g., "hive"
    - # e.g., "supabase_flutter"

env:
  flutter_version: # e.g., "3.22.0"
  dart_version: # e.g., "3.2.0"
```

## `story-xxx.md` — User Story template

```markdown
---
id: user-story-unique-id
title: Название сценария
status: ready  # draft | ready | deprecated
tags: [ux, finance, transaction]
actor: trader
goal: Briefly the goal of the user from goals.md
tech_context: ../.tech_context.yaml
---

## 💬 User Story

As a *trader*, I want to *action*, so that I can *goal*.

## 🔹 Контекст

- When is it used?
- Why is it important to the user?

## 🔗 Привязанные фичи

- [ ] feature-xxx
- [ ] feature-yyy

## 🔐 Ограничения / Бизнес-правила

- Только авторизованные пользователи
- Поддерживаются только определённые валюты
```

## `feature.md` — шаблон фичи

```markdown
---
id: feature-unique-id
title: Название фичи
based_on: user-story-id
status: draft  # draft | ready | in-progress | done
priority: medium  # low | medium | high
component: НазваниеКомпонента
tags: [ui, flutter, form]
tech_context: ../.tech_context.yaml
---

## 🧠 Описание

Опиши, что делает эта фича, как выглядит поведение пользователя.

## 📥 Входные данные

Перечисли, какие данные поступают (от пользователя, от API и т.п.)

## 📤 Выход

Какие данные формируются, куда передаются.

## 🔗 Зависимости

- [ ] Другие фичи / задачи
- [ ] Данные
- [ ] Компоненты

## ✅ Acceptance Criteria

- [ ] Пользователь может ...
- [ ] Валидация происходит ...
- [ ] После отправки ...
```

## `task.md` — шаблон задачи для AI

```markdown
---
id: task-ui-unique-id
title: Название задачи
type: ai-task  # или manual-task
based_on: feature-unique-id
status: draft  # draft | ready | in-progress | done
output: НазваниеВыхода  # StatelessWidget | Class | Function | API endpoint
tags: [flutter, ui, async]
tech_context: ../.tech_context.yaml
---

## 🎯 Цель

Что именно должен сгенерировать AI. Например: UI-форма с валидацией и кнопкой отправки.

## 🔹 Входные параметры

| Имя     | Тип     | Обязательный | Описание                   |
|---------|---------|--------------|-----------------------------|
| amount  | number  | ✅           | Сумма                      |
| note    | string  | ❌           | Комментарий пользователя   |

## ⚙️ Ограничения

- Без использования сторонних библиотек
- Только StatelessWidget
- Обработчик `onSave()` должен быть вызван при нажатии кнопки

## 🧩 Слой архитектуры

`presentation > widgets > form`

## ✅ Критерии успешности

- [ ] AI сгенерировал работающий код
- [ ] Входные поля валидируются
- [ ] Данные отправляются в репозиторий
```

## `component.md` — шаблон для документации компонента

```markdown
---
id: component-expense-form
title: ExpenseForm
type: UI  # UI | logic | data | service | hook | widget
language: dart
status: implemented  # draft | in-progress | implemented | deprecated
used_in: [feature-expense-form, task-ui-expense-form]
layer: presentation
tech_context: ../.tech_context.yaml
tags: [flutter, stateless, form]
---

## 🧩 Описание

Форма для ввода трат: сумма, категория, комментарий. Используется на экране добавления транзакции.

## 📥 Props / Inputs

| Имя       | Тип     | Обязательный | Описание                |
|-----------|---------|--------------|--------------------------|
| onSave    | Func    | ✅           | Колбэк при отправке формы |
| category  | String  | ❌           | Значение по умолчанию   |

## 📤 Выходные данные

- Вызов `onSave(Map<String, dynamic>)` при валидации
- Возврат валидных данных из всех полей

## 🔗 Зависимости

- flutter/material.dart
- `SaveExpense` logic task
- `ExpenseModel` (data/domain)

## 🧪 Тесты / проверка

- [ ] Поля отображаются
- [ ] Валидация работает
- [ ] Данные передаются наружу

## 💡 Примечания

Можно переиспользовать для редактирования существующей записи (с префилом).
```

### 💼 Расширения по слоям

| Layer | Пример компонента |
| --- | --- |
| `presentation` | `ExpenseForm`, `ChartCard` |
| `application` | `SaveExpense`, `Notifier` |
| `domain` | `ExpenseModel`, `UseCase` |
| `data` | `ExpenseRepository`, `API` |