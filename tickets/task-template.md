# ManaSync Task Template

Use this template for all new task entries so PRs remain consistent across phases.

### [TASK-ID]

#### 1. Task Metadata

```text
Task ID: P?-???
Type: Feature/Bugfix/Refactor/Config/Test
Priority: Critical/High/Medium/Low
Estimate: S/M/L/XL
```

#### 2. Pull Request Information

```text
PR Title: feat|fix|chore|test: concise-description
Branch Name: feature|fix/descriptive-name
```

#### 3. Detailed Description

- Objective: [What problem this solves]
- Scope: [What is included]
- Scope Excluded: [What is not included]
- Technical Context: [Vertical Slice files/modules]

#### 4. Acceptance Criteria

```text
- GIVEN [initial state]
  WHEN [action]
  THEN [expected outcome]
```

#### 5. Implementation Instructions

```bash
# Step 1: Sync with main
git checkout main
git pull origin main

# Step 2: Create branch
git checkout -b [branch-name]

# Step 3: Development steps
0. Update README.md "Data Model Diagram" (Mermaid) with any entity/relationship/field decisions introduced in this task.
1. [Technical action]
2. [Technical action]
3. [Technical action]
```

#### 6. Expected File Structure

```text
src/
├── features/[feature-name]/
│   ├── components/
│   ├── stores/
│   ├── services/
│   ├── types/
│   └── __tests__/
```

#### 7. Testing Requirements

##### Unit Tests (Vitest)

```typescript
describe('[Unit Under Test]', () => {
  it('should [expected behavior]', () => {
    // Arrange, Act, Assert
  });
});
```

##### E2E Tests (Playwright/Cypress)

```typescript
test('[Flow name]', async ({ page }) => {
  // Setup, Actions, Assertions
});
```

##### Required Configuration

- [ ] Vitest config for unit tests
- [ ] Playwright/Cypress setup for E2E
- [ ] GitHub Actions workflow for CI/CD

#### 8. Manual Testing Steps

```text
1. [Precise command or UI action]
2. [Expected verification]
3. [Edge case]
```

#### 9. Dependencies

```text
Depends on: [Task IDs]
Blocks: [Task IDs]
```

#### 10. CI/CD Configuration

```yaml
name: [workflow-name]
on: [push, pull_request]
jobs:
  test:
    steps:
      - Run linter
      - Run unit tests
      - Run E2E tests
      - Build check
```

#### 11. Definition of Done

- [ ] Code implemented per acceptance criteria
- [ ] Unit tests written and passing (>80% coverage)
- [ ] E2E tests for critical flows
- [ ] README Data Model Diagram updated for entity/relationship/field changes
- [ ] Documentation updated (JSDoc, README if applicable)
- [ ] Linter passing (ESLint + Prettier)
- [ ] TypeScript with no errors (`npm run type-check`)
- [ ] Successful build (`npm run build`)
- [ ] PR approved by at least 1 reviewer
- [ ] Merged to `main` without conflicts
