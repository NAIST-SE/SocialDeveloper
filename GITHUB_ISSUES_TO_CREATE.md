# GitHub Issues to Create

This file contains templates for creating GitHub issues for each problem found and fixed in the repository.

---

## Issue #1: Corrupted .gitignore file

**Labels:** `bug`, `documentation`  
**Status:** Fixed but issue should remain open for tracking

**Title:**  
Fix corrupted .gitignore file containing vim control sequences

**Description:**  
The `.gitignore` file was corrupted with vim/terminal control sequences, likely from accidentally opening the binary `.DS_Store` file in vim. The file contained escape sequences and binary data instead of proper gitignore patterns.

**Root Cause:**  
Opening binary files (`.DS_Store`) in text editors like vim can inject control sequences into files.

**Fix Applied:**  
- ✅ Removed corrupted `.gitignore` file
- ✅ Created new `.gitignore` with proper patterns including:
  - `.DS_Store` and macOS system files
  - Editor temp files (`.swp`, `.swo`, `*~`)
  - IDE directories (`.vscode/`, `.idea/`)
  - `node_modules/`

**Files Changed:** `.gitignore`

**Commit:** Fixed in PR #[number]

---

## Issue #2: macOS system file committed to repository

**Labels:** `bug`, `cleanup`  
**Status:** Fixed but issue should remain open for tracking

**Title:**  
Remove macOS .DS_Store system file from repository

**Description:**  
A `.DS_Store` file (macOS Desktop Services Store - a system file) was committed to the repository. This file should not be in version control as it's OS-specific and contains metadata about folder view settings that are not relevant to the project.

**Impact:**  
- Unnecessary file in repository
- Can cause merge conflicts
- Adds bloat to repository history

**Fix Applied:**  
- ✅ Removed `.DS_Store` file using `git rm`
- ✅ Added `.DS_Store` to `.gitignore` to prevent future commits

**Files Changed:** `.DS_Store` (removed), `.gitignore` (updated)

**Commit:** Fixed in PR #[number]

---

## Issue #3: Typo in GitHub Actions workflow file

**Labels:** `bug`, `github-actions`  
**Status:** Fixed but issue should remain open for tracking

**Title:**  
Fix typo in .github/workflows/automerge.yaml - missing 'n' in 'name'

**Description:**  
Line 1 of `.github/workflows/automerge.yaml` has a typo: `ame: Pull Request Auto Merge` instead of `name: Pull Request Auto Merge`. The missing 'n' causes the workflow name field to be malformed.

**Impact:**  
- GitHub Actions may not properly recognize the workflow name
- Confusing workflow display in GitHub UI

**Fix Applied:**  
- ✅ Changed `ame:` to `name:` on line 1

**Files Changed:** `.github/workflows/automerge.yaml`

**Commit:** Fixed in PR #[number]

---

## Issue #4: Extensive duplicate entries in Contributors.md

**Labels:** `bug`, `data-quality`, `high-priority`  
**Status:** Fixed but issue should remain open for tracking

**Title:**  
Remove all duplicate entries from Contributors.md

**Description:**  
Contributors.md file contained extensive duplicate entries throughout the file. Analysis revealed:

**Statistics:**
- Total lines before: 683
- Unique lines: 567
- Duplicate entries: 96 different entries had duplicates
- Total duplicates removed: 116 lines

**Notable Examples:**
- Student 2511280 (Hinata Mamoru) appeared 2 times
- Student 2511324 (Daisuke Watanabe) appeared 2 times
- Student 2411314 (Miku Watanabe) appeared 2 times
- Student 2011017 (Ikegami Ayano) appeared 6 times
- Many students from earlier years (1911xxx, 2011xxx, 2111xxx series) had multiple duplicate entries

**Root Cause:**  
This issue likely resulted from multiple PRs being merged without checking for existing entries. The automerge workflows may have contributed to this by merging PRs automatically without validation.

**Recommended Prevention:**  
1. Add a CI check to validate Contributors.md has no duplicates before merging
2. Update contribution guidelines to instruct contributors to search for existing entries
3. Consider a script that automatically checks for duplicates

**Fix Applied:**  
- ✅ Used deduplication algorithm (`awk '!seen[$0]++'`) to remove all duplicate lines while preserving first occurrence
- ✅ Reduced file from 683 lines to 567 unique lines
- ✅ Removed 116 duplicate entries total
- ✅ Verified zero remaining duplicates

**Files Changed:** `Contributors.md`

**Commit:** Fixed in PR #[number]

---

## Issue #5: Missing file extensions for documentation files

**Labels:** `enhancement`, `documentation`  
**Status:** Fixed but issue should remain open for tracking

**Title:**  
Add .md extension to documentation files for clarity

**Description:**  
Several files in the repository lack file extensions, making it unclear what format they are in. This affects:
- Editor syntax highlighting
- GitHub rendering
- File type detection
- IDE functionality

**Files Affected:**
- `code_of_conduct` (Markdown content) → renamed to `code_of_conduct.md`
- `PotentialPR` (Markdown content) → renamed to `PotentialPR.md`
- `SE-class-2021` (text content) → renamed to `SE-class-2021.md`
- `SE-class-2022` (text content) → renamed to `SE-class-2022.md`
- `SE-class-2023` (text content) → renamed to `SE-class-2023.md`
- `SE-class-2024` (text content) → renamed to `SE-class-2024.md`
- `SE-class-2025` (text content) → renamed to `SE-class-2025.md`

**Impact:**  
- Better GitHub rendering with proper Markdown formatting
- Improved editor experience with syntax highlighting
- Clearer file type indication for contributors

**Fix Applied:**  
- ✅ Renamed all 7 files to include `.md` extension
- ✅ Verified files render properly in GitHub

**Files Changed:** 7 files renamed

**Commit:** Fixed in PR #[number]

---

## Summary for Repository Maintainer

**Total Issues Identified:** 5  
**All Issues Fixed:** ✅ Yes  
**Severity:** Medium to High (Issue #4 particularly severe with 116 duplicates)

**Action Items for Maintainers:**
1. Create these 5 GitHub issues manually (automated agent lacks permissions)
2. Review and merge the PR that fixes all issues
3. Consider implementing CI checks to prevent future duplicates in Contributors.md
4. Update contribution guidelines about checking for existing entries
5. Keep issues open for tracking/documentation purposes as requested

**Documentation:**  
See `ISSUES_IDENTIFIED.md` for detailed technical information about each issue and fix.
