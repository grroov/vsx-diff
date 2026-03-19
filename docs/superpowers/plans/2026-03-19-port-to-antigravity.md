# Port to Antigravity Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Rebrand the "Diff Folders" extension to "Antigravity" for all user-facing text while maintaining technical compatibility.

**Architecture:** Systematic replacement of "Visual Studio Code" and "VS Code" with "Antigravity" in metadata, documentation, and source code strings.

**Tech Stack:** Node.js, TypeScript, VS Code Extension API.

---

### Task 1: Update Metadata (package.json)

**Files:**
- Modify: `package.json`

- [ ] **Step 1: Update displayName, description, and top-level titles**
Update `displayName`, `description`, `contributes.viewsContainers.activitybar[0].title`, and `contributes.configuration.title` to use "Antigravity".

- [ ] **Step 2: Update command titles and categories**
Update all command titles and `category` fields in `contributes.commands` that reference "Diff Folders" (e.g., "Diff Folders" -> "Antigravity Diff Folders").

- [ ] **Step 3: Verify package.json**
Run: `grep -Ei "VS Code|Visual Studio Code" package.json`
Expected: Only technical references in `engines` or `devDependencies` should remain.

- [ ] **Step 4: Commit**

```bash
git add package.json
git commit -m "feat: update metadata for Antigravity"
```

---

### Task 2: Update Documentation (README.md & CHANGELOG.md)

**Files:**
- Modify: `README.md`
- Modify: `CHANGELOG.md`

- [ ] **Step 1: Replace branding in README.md**
Perform a global replacement of "Visual Studio Code" and "VS Code" with "Antigravity", preserving the "Projects" links.

- [ ] **Step 2: Replace branding in CHANGELOG.md**
Perform a global replacement of "Visual Studio Code" and "VS Code" with "Antigravity", excluding historical issue URLs.

- [ ] **Step 3: Verify documentation**
Run: `grep -Ei "VS Code|Visual Studio Code" README.md CHANGELOG.md | grep -v "L13RARY.l13-projects" | grep -v "microsoft/vscode/issues"`
Expected: No branding references should remain outside of excluded links.

- [ ] **Step 4: Commit**

```bash
git add README.md CHANGELOG.md
git commit -m "docs: rebrand documentation to Antigravity"
```

---

### Task 3: Update Source Code Branding

**Files:**
- Modify: `src/services/panel/DiffPanel.ts`
- Modify: `src/services/output/DiffOutput.ts`
- Modify: `src/services/output/DiffStatusBar.ts`

- [ ] **Step 1: Update DiffPanel.ts**
Replace "Diff Folders" in the WebView title, HTML `<title>` tag, and any default panel title constants.

- [ ] **Step 2: Update DiffOutput.ts**
Replace "Diff Folders" in the Output channel name.

- [ ] **Step 3: Update DiffStatusBar.ts**
Replace "Diff Folders" in the Status bar tooltip and text.

- [ ] **Step 4: Verify code strings**
Run: `grep -rnEi "VS Code|Visual Studio Code|Diff Folders" src/services/`
Expected: Only `import * as vscode` and technical API calls should remain.

- [ ] **Step 5: Run build and lint to ensure integrity**
Run: `npm run compile && npm run check-lint-rules`
Expected: Both commands finish successfully.

- [ ] **Step 6: Commit**

```bash
git add src/services/panel/DiffPanel.ts src/services/output/DiffOutput.ts src/services/output/DiffStatusBar.ts
git commit -m "feat: rebrand source code strings"
```
