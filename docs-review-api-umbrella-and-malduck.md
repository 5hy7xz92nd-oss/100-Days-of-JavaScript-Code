# Documentation Review: API Umbrella & Malduck

Review of documentation quality, broken links, and content issues for two open-source project READMEs.

---

## 1. API Umbrella

### Link Health Check

| URL | Status | Notes |
|-----|--------|-------|
| `https://api-umbrella.readthedocs.org/en/latest/getting-started.html` | **403 Forbidden** | Docs appear to be down or removed from ReadTheDocs |
| `https://api-umbrella.readthedocs.org/en/latest/developer/dev-setup.html` | **403 Forbidden** | Same as above |
| `https://api.data.gov/` | **200 OK** | Working - GSA API management service |
| `http://developer.nrel.gov/` | **503 Service Unavailable** | Site is down |
| `https://api.sam.gov` | **404 Not Found** | Page not found |
| `https://github.com/NREL/api-umbrella/blob/master/README.md` | **200 OK** | Working |
| `https://github.com/NREL/api-umbrella/blob/master/LICENSE.txt` | **200 OK** | Working - MIT License |

**Summary:** 4 of 7 links are broken or unavailable. The `.io` variant (`api-umbrella.readthedocs.io`) also returns 403, confirming the ReadTheDocs documentation is no longer hosted.

### Grammar / Typos

1. **"is already taken care if the API is being accessed"** - should be **"taken care *of* if"** (missing word "of").
2. **"All your APIs are can be accessed"** - should be **"All your APIs *can* be accessed"** (extra word "are").

### Content Issues

1. **ReadTheDocs links use `.org` domain** - ReadTheDocs migrated to `.io` years ago. However, even the `.io` variants return 403, indicating the documentation is entirely unavailable. The project may need to re-deploy its docs or host them elsewhere.
2. **NREL Developer Network link uses HTTP** - `http://developer.nrel.gov/` should use HTTPS for security. However, the site is currently returning 503 regardless.
3. **api.sam.gov link has no path** - The bare domain `https://api.sam.gov` returns 404. The correct URL may have changed (e.g., `https://sam.gov/` or a specific API endpoint).
4. **"Who's using API Umbrella?" section is outdated** - 2 of the 3 listed users have non-functional links, suggesting the list hasn't been maintained.
5. **"Edit this file" link** - Points to GitHub for community edits, which is a good practice but relies on the project being actively maintained.

### Structural Observations

- The README is well-organized with clear sections for different audiences (creators vs. consumers).
- The dual-perspective approach (API creators and API consumers) is effective.
- Missing: version/release information, installation instructions, or a quickstart code example.

---

## 2. Malduck

### Link Health Check

| URL | Status | Notes |
|-----|--------|-------|
| `https://malduck.readthedocs.io/en/latest/` | **403 Forbidden** | Docs appear to be down or removed |
| `https://malduck.readthedocs.io/en/stable/` | **403 Forbidden** | Same as above |
| `https://github.com/hatching/roach` | **200 OK** | Working - Roach project |
| `https://github.com/mak/mlib` | **200 OK** | Working - mlib library |
| `https://lokalhost.pl` | **503 Service Unavailable** | Site is down |
| `https://cuckoosandbox.org/` | **503 Service Unavailable** | Site is down |
| `https://www.cert.pl/uploads/2019/02/en_horizontal_cef_logo-e1550495232540.png` | **200 OK** | Image accessible |

**Summary:** 4 of 7 links are broken or unavailable. Both ReadTheDocs documentation links are inaccessible.

### Typos / Naming Issues

1. **"Camelie"** in the features list should be **"Camellia"** (the block cipher is spelled "Camellia").

### Content Issues

1. **Both ReadTheDocs links are broken** - The README links to both `/en/latest/` and `/en/stable/` variants, and both return 403. Users have no way to access the referenced documentation.
2. **Redundant documentation links** - The "How to start" section has two nearly identical sentences:
   - "More documentation can be found on readthedocs"
   - "Usage documentation can be found on readthedocs"
   These point to `/latest/` and `/stable/` respectively but should be consolidated or differentiated more clearly.
3. **Inconsistent API parameter ordering in examples** - The AES example uses `encrypt(key, iv, plaintext)` while Serpent uses `encrypt(key, plaintext, iv)`. If this is intentional (different APIs), it should be called out explicitly to avoid confusing users. If it's a typo, one of them should be corrected.
4. **lokalhost.pl and cuckoosandbox.org are down** - Both external project links return 503. These are contextual/historical references so they're less critical, but worth noting.
5. **CEF logo image** - The EU co-financing logo at the bottom is from 2019 and hosted on cert.pl. If the funding period has ended, this may no longer be required or accurate.

### Structural Observations

- Good use of code examples for each major feature area.
- The heading hierarchy is slightly inconsistent: "AES" uses `####` (h4) while "Serpent" and others use `###` (h3).
- The navigation link at the top (`[Installation]` / `[Docs]`) is a nice touch.
- The extractor engine example is thorough and shows real-world usage patterns.
- Missing: a badge for PyPI version, Python version compatibility, or CI status.

---

## Overall Recommendations

### Critical (both projects)

1. **Fix or replace ReadTheDocs links** - All four ReadTheDocs URLs across both projects return 403. This is the most impactful issue as it cuts off users from detailed documentation.

### High Priority

2. **API Umbrella: Fix grammar errors** - Two grammatical errors ("taken care if" and "are can be") hurt credibility.
3. **Malduck: Fix "Camelie" typo** - Should be "Camellia".
4. **API Umbrella: Update or remove dead links** in "Who's using API Umbrella?" section.

### Medium Priority

5. **Malduck: Clarify parameter ordering** difference between AES and Serpent examples.
6. **Malduck: Fix heading hierarchy** - Make AES example heading consistent with other examples.
7. **Malduck: Consolidate redundant documentation links** at the bottom.
8. **API Umbrella: Upgrade HTTP links to HTTPS** where applicable.

### Low Priority

9. **Both: Add project status badges** (build status, version, license) for at-a-glance health.
10. **API Umbrella: Add quickstart code example** to complement the link to the getting-started guide.
