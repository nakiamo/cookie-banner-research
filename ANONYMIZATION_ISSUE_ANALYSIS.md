# Anonymization Issue Analysis: GitHub URLs in Website Prototypes

**Date:** 2025-12-29  
**Issue:** GitHub username visible in website prototype HTML files  
**Severity:** ⚠️ **HIGH** - Breaks blind review anonymization

---

## Problem Identified

### Issue Location
All four `index.html` files in `02_experimental_materials/website_prototypes/` contain hardcoded GitHub Pages URLs that include the username **"nakiamo"**.

### Specific Findings

**Starbucks Prototypes** (starbucks_consistent & starbucks_mismatched):
- URLs contain: `https://nakiamo.github.io/experiment-1/assets/images/...`
- Found in:
  - Background images (CSS)
  - Image `src` attributes (HTML)
  - Total: ~4-5 references per file

**Coffee Bean House Prototypes** (coffeebean_consistent & coffeebean_mismatched):
- URLs contain: `https://nakiamo.github.io/experiment-3/assets/images/...`
- Found in:
  - Background images (CSS)
  - Image `src` attributes (HTML)
  - Total: ~6-7 references per file

### Example References Found:
```html
<!-- Starbucks -->
background-image: url('https://nakiamo.github.io/experiment-1/assets/images/starbucks-1.jpg');
<img src="https://nakiamo.github.io/experiment-1/assets/images/starbucks-for-life-spring.jpg">

<!-- Coffee Bean House -->
background-image: url('https://nakiamo.github.io/experiment-3/assets/images/espresso-house-1.jpg');
<img src="https://nakiamo.github.io/experiment-3/assets/images/coffeebean-house-logo.svg">
```

---

## Logical Interpretation

### Why This Is a Problem

1. **Direct Identity Exposure:**
   - The username "nakiamo" is visible in the HTML source code
   - Reviewers can easily see this when inspecting the website prototypes
   - This directly identifies the author, breaking blind review requirements

2. **Potential for Further Investigation:**
   - Reviewers could visit `https://nakiamo.github.io/experiment-1/` or `experiment-3/`
   - These GitHub Pages sites may contain additional identifying information
   - Could lead to discovery of other repositories or personal information

3. **Blind Review Violation:**
   - Journals require complete anonymization for blind review
   - Any identifying information (including GitHub usernames) must be removed
   - This could result in manuscript rejection or review delay

4. **Scope of Exposure:**
   - **4 files affected:** All website prototype HTML files
   - **~20 total references:** Multiple instances per file
   - **All reviewers:** Anyone accessing the anonymous repository can see this

---

## Impact Assessment

### Current State
- ✅ Repository is anonymized (authors, dates, etc.)
- ✅ Data is anonymized
- ✅ Code is generic
- ❌ **Website prototypes contain identifying GitHub URLs**

### Risk Level: **HIGH**
- Easy to discover (visible in HTML source)
- Direct link to author's GitHub account
- Violates blind review requirements
- Could compromise entire anonymization effort

---

## Solution Options

### Option 1: Replace with Relative Paths (RECOMMENDED)
**Approach:** Change all GitHub Pages URLs to relative paths
- `https://nakiamo.github.io/experiment-1/assets/images/...` 
- → `assets/images/...`

**Pros:**
- ✅ Complete anonymization
- ✅ Files work locally and in repository
- ✅ No external dependencies
- ✅ Maintains functionality

**Cons:**
- ⚠️ Requires updating all 4 HTML files
- ⚠️ Need to ensure all images are in local `assets/images/` folders

**Implementation:**
- Replace all `https://nakiamo.github.io/experiment-X/` with relative paths
- Verify all images exist in local `assets/images/` folders
- Test that prototypes still work correctly

---

### Option 2: Use Anonymous GitHub Pages URLs
**Approach:** Create anonymous GitHub Pages hosting

**Pros:**
- ✅ Maintains external hosting
- ✅ No local file changes needed

**Cons:**
- ❌ Requires creating new anonymous GitHub account
- ❌ More complex setup
- ❌ Still relies on external service

---

### Option 3: Remove Website Prototypes from Repository
**Approach:** Remove the website prototypes entirely

**Pros:**
- ✅ Complete removal of identifying information

**Cons:**
- ❌ Reduces reproducibility
- ❌ Reviewers can't see experimental materials
- ❌ May violate data sharing requirements

---

## Recommendation

**Option 1 (Relative Paths)** is the best solution because:
1. ✅ Complete anonymization
2. ✅ Maintains full functionality
3. ✅ All images are already in local folders
4. ✅ Simple to implement
5. ✅ No external dependencies

---

## Files Requiring Changes

1. `02_experimental_materials/website_prototypes/starbucks_consistent/index.html`
2. `02_experimental_materials/website_prototypes/starbucks_mismatched/index.html`
3. `02_experimental_materials/website_prototypes/coffeebean_consistent/index.html`
4. `02_experimental_materials/website_prototypes/coffeebean_mismatched/index.html`

**Total references to replace:** ~20 instances

---

## Next Steps

1. **Decision:** Choose solution approach
2. **Implementation:** Update HTML files
3. **Verification:** Test that prototypes work correctly
4. **Commit:** Update repository with anonymized versions
5. **Push:** Update anonymous repository

---

**Status:** ⚠️ **AWAITING DECISION** - Ready to implement once solution is chosen

