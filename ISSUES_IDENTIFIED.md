# Repository Issues Identified and Fixed

This document lists all issues found in the repository and their resolutions. Each issue should be created as a separate GitHub issue.

## Issue 1: Corrupted .gitignore file

**Title:** Fix corrupted .gitignore file containing vim control sequences

**Description:**
The `.gitignore` file was corrupted with vim/terminal control sequences, likely from accidentally opening the binary `.DS_Store` file in vim. The file contained escape sequences and binary data instead of proper gitignore patterns.

**Status:** ✅ FIXED
**Fix Applied:** 
- Removed corrupted `.gitignore` file
- Created new `.gitignore` with proper patterns including:
  - `.DS_Store` and macOS system files
  - Editor temp files (`.swp`, `.swo`, `*~`)
  - IDE directories (`.vscode/`, `.idea/`)
  - `node_modules/`

**Files Changed:** `.gitignore`

---

## Issue 2: macOS .DS_Store file committed to repository

**Title:** Remove macOS .DS_Store system file from repository

**Description:**
A `.DS_Store` file (macOS Desktop Services Store - a system file) was committed to the repository. This file should not be in version control as it's OS-specific and contains metadata about folder view settings.

**Status:** ✅ FIXED
**Fix Applied:**
- Removed `.DS_Store` file using `git rm`
- Added `.DS_Store` to `.gitignore` to prevent future commits

**Files Changed:** `.DS_Store` (removed)

---

## Issue 3: Typo in automerge.yaml workflow file

**Title:** Fix typo in .github/workflows/automerge.yaml - missing 'n' in 'name'

**Description:**
Line 1 of `.github/workflows/automerge.yaml` has a typo: `ame: Pull Request Auto Merge` instead of `name: Pull Request Auto Merge`. The missing 'n' causes the workflow name field to be malformed.

**Status:** ✅ FIXED
**Fix Applied:**
- Changed `ame:` to `name:` on line 1

**Files Changed:** `.github/workflows/automerge.yaml`

---

## Issue 4: Extensive duplicate entries in Contributors.md

**Title:** Remove all duplicate entries from Contributors.md

**Description:**
Contributors.md file contained extensive duplicate entries throughout the file. Analysis revealed:
- Total lines: 683
- Unique lines: 567
- Duplicate entries: 96 different entries had duplicates

Notable duplicates included:
- Student 2511280 (Hinata Mamoru) appeared twice
- Student 2511324 (Daisuke Watanabe) appeared twice
- Student 2411314 (Miku Watanabe) appeared twice
- Many students from earlier years (1911xxx, 2011xxx, 2111xxx series) had multiple duplicate entries
- Some students appeared up to 6 times (e.g., 2011017 - Ikegami Ayano)

This issue likely resulted from multiple PRs being merged without checking for existing entries.

**Status:** ✅ FIXED
**Fix Applied:**
- Used deduplication algorithm to remove all duplicate lines while preserving first occurrence
- Reduced file from 683 lines to 567 unique lines
- Removed 116 duplicate entries total
- Verified zero remaining duplicates

**Files Changed:** `Contributors.md`

---

## Issue 5: Missing file extensions for documentation files

**Title:** Add .md extension to documentation files for clarity

**Description:**
Several files in the repository lack file extensions, making it unclear what format they are in:
- `code_of_conduct` (Markdown content)
- `PotentialPR` (Markdown content)
- `SE-class-2021` (text content)
- `SE-class-2022` (text content)
- `SE-class-2023` (text content)
- `SE-class-2024` (text content)
- `SE-class-2025` (text content)

**Status:** ✅ FIXED
**Fix Applied:**
- Renamed `code_of_conduct` to `code_of_conduct.md`
- Renamed `PotentialPR` to `PotentialPR.md`
- Renamed `SE-class-2021` to `SE-class-2021.md`
- Renamed `SE-class-2022` to `SE-class-2022.md`
- Renamed `SE-class-2023` to `SE-class-2023.md`
- Renamed `SE-class-2024` to `SE-class-2024.md`
- Renamed `SE-class-2025` to `SE-class-2025.md`

**Files Changed:** All 7 files renamed

---

## Summary

**Total Issues Found:** 5
**Issues Fixed:** 5 (100%)

**Categories:**
- File corruption: 1 issue
- System files in repository: 1 issue
- Syntax errors: 1 issue
- Duplicate data: 1 issue (extensive - 116 duplicates removed)
- Missing file extensions: 1 issue

All issues have been identified and corrected in this pull request.
