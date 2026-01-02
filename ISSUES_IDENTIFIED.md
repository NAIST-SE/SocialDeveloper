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

## Issue 4: Duplicate entry for student 2511280 in Contributors.md

**Title:** Remove duplicate entry for student 2511280 (Hinata Mamoru) in Contributors.md

**Description:**
Student 2511280 (Hinata Mamoru) appears twice in the Contributors.md file:
- Line 7: `2511280 - Hinata Mamoru - mamoru4949<br/>`
- Line 34: `2511280 - Hinata Mamoru <br/>` (duplicate)

**Status:** ✅ FIXED
**Fix Applied:**
- Removed duplicate entry on line 34
- Kept the entry on line 7 (has more information with GitHub username)

**Files Changed:** `Contributors.md`

---

## Issue 5: Duplicate entry for student 2511324 in Contributors.md

**Title:** Remove duplicate entry for student 2511324 (Daisuke Watanabe) in Contributors.md

**Description:**
Student 2511324 (Daisuke Watanabe) appears twice in the Contributors.md file:
- Line 31: `2511324 - Daisuke Watanabe <br/>`
- Line 35: `2511324 - Daisuke Watanabe <br/>` (duplicate)

**Status:** ✅ FIXED
**Fix Applied:**
- Removed duplicate entry on line 35
- Kept the entry on line 31

**Files Changed:** `Contributors.md`

---

## Issue 6: Duplicate entry for student 2411314 in Contributors.md

**Title:** Remove duplicate entry for student 2411314 (Miku Watanabe) in Contributors.md

**Description:**
Student 2411314 (Miku Watanabe) appears twice in the Contributors.md file:
- Line 30: `2411314 - Miku Watanabe , mmikuu` (missing `<br/>` tag)
- Line 33: `2411314 - Miku Watanabe , mmikuu <br/>` (duplicate)

Note: There's another entry on line 524 but with different format (`2411314 - Miku Watanabe <br/>`), which appears to be a separate contribution.

**Status:** ✅ FIXED
**Fix Applied:**
- Removed duplicate entry on line 33
- Fixed line 30 to add missing `<br/>` tag
- Kept the entry on line 524 as it appears to be a different contribution

**Files Changed:** `Contributors.md`

---

## Issue 7: Missing file extensions for documentation files

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

**Total Issues Found:** 7
**Issues Fixed:** 7 (100%)

**Categories:**
- File corruption: 1 issue
- System files in repository: 1 issue
- Syntax errors: 1 issue
- Duplicate data: 3 issues
- Missing file extensions: 1 issue

All issues have been identified and corrected in this pull request.
