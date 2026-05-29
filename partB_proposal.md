# Part B: Sourcing Strategy + Scale-Up Proposal
## DeepThought Business Analytics Assignment

---

## Question 1: Sourcing Methods — How Else to Find Federer Companies Across India

### Method 1: DSIR In-House R&D Unit Directory
**What it is:** The Department of Scientific and Industrial Research publishes a PDF directory (~1900 companies) of all firms with government-recognized R&D units. Updated annually. Publicly downloadable.

**Why it works for this ICP:** DSIR recognition is an imperfect but powerful Federer signal:
- Requires dedicated R&D lab + staff → indicates C4 (technical mindset)
- Requires in-house technology focus → filters against service companies and traders
- DSIR companies get R&D tax benefits → only genuine R&D performers apply

**How to use:** Parse the PDF, filter by city, cross-reference against segment (industry classification codes) and revenue data.

**Limitations:** Directory doesn't include revenue bands. Many large companies (Divi's, Laurus) are included. Needs revenue filtering step. Some small companies are included that are just doing basic R&D. Also doesn't cover companies that do in-house R&D without formal DSIR recognition.

---

### Method 2: MCA21 / Tofler Revenue + Industry Screener
**What it is:** Ministry of Corporate Affairs company registry, accessible via Tofler. Every registered company in India has financials filed. Can filter by NIC Industry Code + Revenue Range + State.

**Why it works:** Revenue bands are verifiable (from filed accounts). NIC codes map roughly to specialty segments (e.g., NIC 2100 = pharma, NIC 2010 = basic chemicals — need sub-code refinement). Allows building a raw universe of Rs.50–500Cr manufacturers by segment and city.

**Limitations:** NIC codes are coarse — NIC 2100 includes both generic API manufacturers and specialty biotech companies. Needs a second-pass qualification step. Tofler API access is paid (~Rs.10-15 per company).

---

### Method 3: BioAsia / CPHI India / CHEMTECH Attendee and Exhibitor Lists
**What it is:** Major Indian industry conferences:
- **BioAsia** (Hyderabad — annual) — life sciences, biotech, pharma
- **CPHI India** (Mumbai — annual) — API, CDMO, finished dosage
- **CHEMTECH** (Mumbai) — specialty chemicals
- **Fi India / Vitafoods** — nutraceutical/food ingredients

**Why it works:** Exhibitors are almost always manufacturers (not service labs). Speaker lists reveal technical decision-makers. Companies paying for exhibition stands are almost certainly in growth mode (C6 signal). Conference segment classification is already pre-filtered.

**How to use:** Scrape exhibitor lists from conference websites year-by-year (2022-2025 available). Cross-reference against location and revenue.

**Limitations:** Skews toward companies that can afford exhibition spend (Rs.30Cr+ minimum). Very small companies (<Rs.20Cr) may not exhibit. Some conference lists are behind paywalls.

---

### Method 4: PLI Scheme Beneficiary Databases
**What it is:** Government has published beneficiary lists for PLI (Production-Linked Incentive) schemes in pharmaceuticals, medical devices, food processing, and specialty chemicals. These are companies that have applied for and/or received PLI benefits.

**Why it works:** PLI eligibility requires: (1) Indian manufacturer, (2) specified minimum investment, (3) incremental production. This is a verified growth signal. The pharma and medical devices PLI specifically requires specialty or high-complexity products — filtering against commodity generics.

**How to use:** DPIIT / MoC&I websites publish beneficiary lists. Cross-reference against city and segment.

**Limitations:** Not all ICP companies participate in PLI (many specialty niche players are too small for minimum thresholds). Large companies also appear. Needs revenue filter overlay.

---

### Method 5: Export Data via EXIM / Volza / Zauba
**What it is:** India's customs export data is commercially available via platforms like Volza, Zauba, ImportYeti. Shows: company name, export value, product HSN code, destination country.

**Why it works for Federer companies:**
- Export to US/EU = likely USFDA/EU-GMP approved manufacturer (C3 signal)
- High-value, small-volume exports = specialty product not commodity
- Consistent year-over-year exports = stable manufacturer not trader
- HSN codes narrow segment identity (e.g., HSN 3002 = vaccines/biologics, HSN 2941 = APIs)

**Limitations:** Export data reflects shipments, not company revenue. Some exporters are trading houses not manufacturers. Requires cross-referencing with company website to verify manufacturing. Subscription cost (Volza ~$300/month).

---

### Method 6: Patent Filing Databases (IP India, Google Patents)
**What it is:** IP India's patent database (free), Google Patents — search for Indian assignees filing patents in target technology areas.

**Why it works:** Patent filings = genuine technical innovation = C3 (differentiated) + C4 (technical DM) signals combined. Companies filing patents are building IP, not just copying. The assignee name reveals the exact company.

**Search strategy:** "assignee country: India AND technology: probiotic strains" or "peptide synthesis" etc. + filter by Hyderabad/Telangana inventor addresses.

**Limitations:** Many Federer companies operate with trade secrets not patents (proprietary strains, process know-how). Patent absence ≠ not differentiated. Also patent applications are public but granted patents take time — recent filings show intent, not proven moat.

---

### Method 7: LinkedIn Sales Navigator — Founder/Director Title + Industry + Company Size
**What it is:** LinkedIn Sales Navigator with filters: Job Title = "Founder/MD/CMD/Chairman", Industry = "Biotechnology/Chemicals/Medical Devices", Company Size = "11-50" or "51-200" employees, Location = target city.

**Why it works:** Directly surfaces the Federer decision-maker (technical founder/MD). Company size acts as a rough revenue proxy for private companies. Education background (IIT/NIT/BITS visible on profiles) is a C4 signal.

**Limitations:** Not all promoters have active LinkedIn profiles (especially older-generation founders). Company size on LinkedIn is self-reported and often stale. Paid subscription required (~$1000/year for Sales Navigator).

---

## Question 2: The 1000-Company Proposal

### Core Approach: Funnel in Four Stages

**Expected funnel:** 5000 candidates → 2000 first-filter → 800 deep-qualified → 1000 by end of month (with quality buffer/resampling built in)

The key insight is: you cannot get 1000 *qualified* companies from a list of 1001 companies. You need a large raw universe (~5000), a fast first-pass filter, and a slower deep-qualification step. The yield rate from experience is ~20-30%, so 1000 qualified requires investigating ~4000-5000.

---

### Week 1: Build the Raw Universe (Days 1-7)

**Goal:** Collect 4000-5000 candidate company names with basic metadata.

**Sources (parallel, not sequential):**
1. **DSIR directory PDF** → Python script to parse and extract: company name, city, industry, validity date → ~1900 entries, filter by target cities and segments → ~500 relevant
2. **Tofler/MCA21 batch pull** → NIC codes for pharma (2100), specialty chemicals (2010/2020), medical devices (3250), food ingredients (1080) + revenue band Rs.50-500Cr + state filter → ~2000 entries
3. **CPHI India + BioAsia + CHEMTECH exhibitor lists (2022-2025)** → Scrape 4 years × 3 conferences → ~800 unique manufacturer names
4. **PLI scheme beneficiary lists** → Download and parse → ~300 entries
5. **Zauba/Volza HSN export data** → Pull top-500 Indian exporters by relevant HSN codes → ~500 entries

**Deduplication and merge:** Use Claude API to fuzzy-match company names across sources, merge into single record with source flags.

**Output:** ~4500 deduplicated company names with: name, city, revenue band (where available), industry code, and source flags.

---

### Week 2: Automated First-Pass Qualification (Days 8-14)

**Goal:** Reduce 4500 to ~1500 companies using automated hard filters.

**Process:**
1. **City filter:** Keep only target manufacturing hubs (Hyderabad, Pune, Ahmedabad, Chennai, Coimbatore, Bengaluru, Indore, Vadodara) — removes ~30%
2. **Revenue filter:** Remove companies with Tofler revenue <Rs.30Cr or >Rs.500Cr where data available — removes another ~25%
3. **Ownership auto-check:** Claude API prompt with company name → web search → extract ownership signals (PE mentions, MNC subsidiary, government enterprise) → flag and remove — removes ~15%
4. **Website check:** Automated site fetch → extract: copyright year, "products" section existence, last press release date → flag companies with no website or inactive sites (>2 years no updates) — removes ~10%

**Automation stack:** Python + Claude API (for web search and entity extraction) + GPT batch classification for ownership signals. Cost: ~$50-100 in API credits for 4500 companies.

**Output:** ~1500 companies passing first-pass filters, each with auto-generated flag summary.

**Quality control at this stage:** Spot-check 50 random companies from the retained list. If error rate >15% (i.e., >7-8 companies clearly should have been filtered), retune the prompts before continuing.

---

### Week 3: Deep Qualification (Days 15-21)

**Goal:** Qualify 1500 candidates to ~1000 ICP-confirmed companies.

**Process:**
Each company gets a structured research pass:
1. **Claude API web search per company:** Feed company name + location → extract C1-C6 evidence → output a JSON scorecard (Weak/Moderate/Strong per criterion + evidence quote)
2. **Founder/DM extraction:** LinkedIn + company About page → extract name, title, education, background
3. **Revenue verification:** Cross-reference Tofler vs RocketReach vs any news mention → settle on revenue band
4. **Growth signal extraction:** LinkedIn job posts + press releases + website news → flag if active 2024-2026

**Prompt design (key):** The Claude API prompt must specify: (a) reject service companies even if they sound technical, (b) reject if PE/foreign ownership detected, (c) flag borderline cases for human review rather than auto-passing. Wrong permissive prompts create false positives that contaminate the list.

**Output:** ~1200 companies with full 6-criterion scorecards; ~200 flagged as borderline for human review.

---

### Week 4: Human Review + Quality Control (Days 22-30)

**Goal:** From ~1200 auto-qualified + 200 borderline, select the 1000 highest-confidence ICP matches.

**Process:**
1. **Review 200 borderline cases personally:** Each takes 10-15 minutes → 200 × 12 min = 40 hours → done in 5 days with focused work
2. **Spot-check auto-qualified companies:** Random sample of 100 from the 1200 auto-qualified → verify at least 85% are genuinely ICP-qualified; if <85%, expand spot-check and re-run qualification on suspect batches
3. **Enrich the final 1000:** Add personalization hook for each company (can be Claude API generated + human reviewed) → the hook is what makes the list usable for outreach
4. **Final validation pass:** Check for recently acquired, recently PE-backed, or recently gone-bankrupt companies in the final list

**Output:** 1000-company ICP-qualified list with full scorecards and personalization hooks.

---

### Realistic Yield Estimates

| Stage | Count | Yield |
|-------|-------|-------|
| Raw universe | 4,500 | 100% |
| After first-pass filters (auto) | 1,500 | 33% |
| After deep qualification (auto) | 1,200 | 27% |
| After human review | 1,000 | 22% |

This 22% final yield from raw universe is consistent with the assignment's stated ~30% yield from the 75-100 that were deeply investigated — the difference is that first-pass automation filters out the obvious failures before deep research.

---

### Risk Factors and Mitigations

**Risk 1: False positives (service companies that pass as manufacturers)**
Mitigation: The web-search prompt explicitly checks for "clients," "CRO," "contract research," "testing service" language. Any company with >3 such signals gets auto-flagged for human review.

**Risk 2: Revenue data missing for private companies**
Mitigation: Use Tofler employee count + industry benchmarks as revenue proxy. Companies with 10-50 employees in pharma are likely Rs.20-80Cr; 50-200 employees is likely Rs.50-300Cr.

**Risk 3: Quality degradation from AI errors at scale**
Mitigation: Regular spot-checks (50 companies per 500 processed). Tune prompts immediately when error rate climbs above 10%.

**Risk 4: Founder background data gaps (many promoters not on LinkedIn)**
Mitigation: Secondary sources — company website About page, BioAsia speaker history, news articles, DSIR directory notes. Mark as "Moderate — DM background unverified" rather than auto-failing.

---

*Proposal by Rakesh — May 2026*
