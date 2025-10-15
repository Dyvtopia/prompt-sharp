
![Prompt# Logo](logo/prompt-sharp.png)

# Prompt# (Prompt Sharp)

**Prompt#** is a collection of ready-to-use GitHub Copilot prompt templates for real-world software development tasks.  
Each file defines the **context**, **mode**, and **tools** that guide Copilot to produce consistent, high-quality results.

---

## Purpose

Prompt# helps teams:
- Standardize how they use GitHub Copilot across projects.
- Automate repetitive or complex AI prompting tasks.
- Ensure consistent code quality, style, and architecture.

---


## Example:

feature-add-endpoint.prompt.md
refactor-clean-architecture.prompt.md
test-generate-unit-tests.prompt.md
review-pr-summary.prompt.md
docs-generate-readme.prompt.md

## Folder Structure

```
prompt-sharp/
│
├── prompts/
│   ├── feature-add-endpoint.prompt.md
│   ├── feature-add-command.prompt.md
│   ├── refactor-clean-architecture.prompt.md
│   ├── test-generate-unit-tests.prompt.md
│   ├── review-pr-summary.prompt.md
│   └── docs-generate-readme.prompt.md
│
└── README.md  ← describes naming convention and usage
```


## Naming Rules

### Format 

[category]-[verb]-[task].prompt.md


| Rule                    | Purpose                                | Example                                               |
| ----------------------- | -------------------------------------- | ----------------------------------------------------- |
| Use lowercase           | Keeps consistency and CLI-friendly     | `feature-add-endpoint.prompt.md`                    |
| Use dash `-` separators | Improves readability and searchability | `refactor-clean-architecture.prompt.md`             |
| Use category prefixes   | Groups similar prompts logically       | `feature`, `refactor`, `test`, `review`, `docs`, etc. |
| Keep task descriptive   | Make it clear what the prompt does     | `generate-unit-tests`, `add-endpoint`, etc.           |
| End with `.prompt.md`   | Identifies it as a Copilot prompt      | `xyz.prompt.md`                                     |

### Recommended Verb Patterns

| Verb        | Use For                                      | Example                                 |
| ----------- | -------------------------------------------- | --------------------------------------- |
| `add`       | Creating new code, files, or features        | `feature-add-endpoint.prompt.md`        |
| `generate`  | Auto-generating code, docs, or tests         | `test-generate-unit-tests.prompt.md`    |
| `refactor`  | Improving existing code                      | `refactor-clean-architecture.prompt.md` |
| `update`    | Minor changes or enhancements                | `docs-update-readme.prompt.md`          |
| `review`    | Code analysis or pull request reviews        | `review-pr-summary.prompt.md`           |
| `summarize` | Text or code summaries                       | `summarize-code.prompt.md`              |
| `explain`   | Explaining logic or architecture             | `explain-service-design.prompt.md`      |
| `validate`  | Static analysis, schema, or rule enforcement | `validate-api-contract.prompt.md`       |


## Contributing

- Create a new prompt under .copilot/prompts/

- Follow the naming convention.

- Keep prompts clear, concise, and focused on one task.

- Submit a pull request.


## License

MIT License © 2025 Prompt#



