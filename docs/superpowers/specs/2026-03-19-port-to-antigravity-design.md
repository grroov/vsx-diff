# Design Spec: Porting "Diff Folders" to Antigravity

This document outlines the strategy for rebranding the VS Code extension "Diff Folders" to target the Antigravity platform.

## 1. Objective
Update the codebase to use "Antigravity" branding for all user-facing text while maintaining technical compatibility with the VS Code extension ecosystem.

## 2. Success Criteria
*   All occurrences of "Visual Studio Code" and "VS Code" in user-facing documentation and metadata are replaced with "Antigravity".
*   Extension functionality remains intact (technical namespaces and APIs are preserved).
*   The build process still works as expected.
*   Links to the "Projects" extension are preserved as per user request.

## 3. Architecture & Components

### 3.1 Metadata (`package.json`)
*   **Rebrand:** `displayName`, `description`, and configuration descriptions.
*   **Preserve:** `name`, `publisher`, `engines`, `main`, and `devDependencies`. These are critical for the extension's identity and its ability to load in the VS Code/Antigravity runtime.

### 3.2 Documentation (`README.md`, `CHANGELOG.md`)
*   **Rebrand:** All text references to the original host editor.
*   **Preserve:** External links to the VS Code Marketplace and the "Projects" extension.
*   **Preserve:** Historical issue numbers in the changelog (e.g., `Issue 170` on GitHub).

### 3.3 Source Code (`src/`)
*   **Rebrand:** Hardcoded strings in `src/services/` that appear in info/error messages or QuickPick menus.
*   **Preserve:** All imports from the `'vscode'` module.
*   **Preserve:** All `vscode.*` API calls.
*   **Preserve:** CSS variables (e.g., `--vscode-sideBar-background`) to ensure theme compatibility.

## 4. Implementation Strategy

### 4.1 Automated Replacement
A targeted search-and-replace will be performed on documentation and metadata files.

### 4.2 Manual Verification
Manual review of source code strings to ensure that branding changes do not accidentally break logic or internal identifiers.

## 5. Testing & Validation
*   **Build:** Run `npm run compile` (gulp build) to ensure no syntax errors were introduced.
*   **Lint:** Run `npm run check-lint-rules` to verify project standards.
*   **Visual Check:** Inspect `package.json` and `README.md` to confirm branding consistency.
