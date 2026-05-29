# Methodology Document — Target Company Research
## DeepThought Business Analytics Assignment
**City: Hyderabad | Segments: Specialty Biotech + Custom Synthesis & Specialty Chemicals**

---

## 1. City Choice Rationale

**Hyderabad** was selected over other options because:
- It is India's "Genome Valley" — a purpose-built life sciences cluster with 200+ companies, giving the highest density of biotech/pharma specialty manufacturers in one geography
- The city has a distinct identity from Mumbai or Ahmedabad chemicals clusters — it skews toward biology-heavy, technically-led companies which maps well to the Federer profile (scientist-founder, DSIR recognition, export-market orientation)
- Personal proximity and research familiarity (I'm based here) means I can verify operational presence more confidently

**City definition applied:** Company counted if founder/R&D/primary manufacturing is in Hyderabad. Registered-only offices in Mumbai or elsewhere were ignored.

---

## 2. Segment Choice Rationale

**Primary: Specialty Biotech (probiotics, enzymes, recombinant proteins, fermentation services)**
- Hyderabad has an outsized cluster here (Genome Valley, Biological E., Bharat Biotech, Sanzyme, Unique Biotech, Lazuline)
- Fermentation-based manufacturers have high technical moat, low Chinese commoditization (unlike bulk APIs), and founder-scientist profiles are common
- Many companies in this segment are private, promoter-led, Rs.30–500Cr range

**Secondary: Custom Synthesis & Specialty Chemicals (pharma intermediates, agrochem intermediates)**
- Natural complement — many Hyderabad chemistry companies supply regulated pharma intermediates
- Differentiation comes from regulatory approvals (USFDA, EU-GMP) rather than just price
- Watch-out: Many look like manufacturers but are actually traders or service CDMO companies

---

## 3. Research Process (Step by Step)

### Step 1 — Build a Universe (100+ candidates)
Sources used:
- **Built In Hyderabad biotech list** (22 companies — gave initial names)
- **DSIR recognized R&D units directory (July 2024)** — filtered by Hyderabad/Telangana to find companies with verified in-house R&D
- **Tofler / Screener.in** — for revenue band verification of public and private companies
- **Tracxn / RocketReach** — for startup-stage companies and founder info
- **LinkedIn** — for founder backgrounds (IIT/PhD/ISRO), job postings (growth signals), company updates
- **Company websites** — copyright year, active news/press sections, product catalogue freshness
- **Google Search operators** — "Hyderabad biotech manufacturer founder promoter 2024 2025 expansion"
- **IndiaMART** — cross-checked that companies listed as manufacturers actually have production (not just trading)
- **BioAsia / Pharma City attendee lists** — for smaller companies not on mainstream lists

### Step 2 — First Filter (60 → ~35 candidates)
Applied hard disqualifiers immediately:
- Revenue > Rs.500Cr → removed Laurus Labs, Aurobindo, Natco, Divi's, Bharat Biotech, Biological E., Granules India
- PE/foreign-owned → removed Gland Pharma (Fosun), Aragen (Quadria Capital PE), Shantha Biotechnics (Sanofi)
- Government-owned → removed MIDHANI (GoI 74%), Indian Immunologicals (NDDB)
- Service company (CRO/lab/CDMO) → removed Vimta Labs, Sai Life Sciences, Aragen, Axis Clinicals, Sapien Biosciences (biobank service)
- No website / single-page placeholder → removed 3 companies with stale sites

### Step 3 — Deep Research (35 → 25 profiled)
For each surviving candidate:
1. Confirmed manufacturing (not just importing/trading) via IndiaMART product listing patterns, DSIR directory, company website production page
2. Verified decision-maker background via LinkedIn, company About pages, press mentions
3. Estimated revenue via Tofler operating revenue range, RocketReach revenue estimate, and news mentions
4. Checked growth signals: 2024-2026 press releases, LinkedIn posts, certifications, hiring posts
5. Checked ownership for PE/institutional flags on Tracxn/Screener

### Step 4 — Verdict Assignment
- **Strong Fit:** Passes all 6 criteria with strong/moderate evidence
- **Fit:** Passes 5 criteria; one is moderate with caveat noted
- **Borderline:** Passes 4 criteria; specific risks flagged (usually revenue too small or differentiation unclear)
- **Fail:** Fails any auto-disqualifier; documented with reason

---

## 4. Key Learnings About the Segment

1. **Fermentation ≠ Fermentation Service:** Hyderabad has both product fermentation companies (Sanzyme, Unique Biotech — these pass) and fermentation-service CRDMOs (Aragen — these fail). The distinction is: does the company own the molecule/strain IP or does it just perform the process for someone else?

2. **DSIR Recognition is a Powerful Signal:** A DSIR-recognized in-house R&D unit means the company has a dedicated lab, a research team, and has been audited by the government. This is a strong proxy for technical capability-building which aligns exactly with the Federer profile.

3. **Genome Valley Companies Skew Large:** The most famous Genome Valley tenants (Bharat Biotech, Biological E., Laurus Labs) are all above Rs.500Cr. The sweet spot of Rs.50–300Cr Federer companies are more likely to be: (a) probiotics/fermentation players, (b) specialty synthesis companies, (c) recombinant protein startups.

4. **Ownership Traps in Hyderabad Pharma:**
   - Many "independent" companies are actually subsidiaries (Divi's Nutraceuticals under Divi's Labs)
   - Some have been PE-acquired recently (Aragen / GVK Biosciences → Quadria Capital 2025)
   - Check Tofler for group parent structure before scoring C4 (Technical DM)

5. **The Service Company Problem:** Hyderabad biotech has many CROs, testing labs, and CDMOs that *look* like manufacturers. Red flags: website mentions "clients," "projects," "studies," or "samples" rather than "products," "batches," "capacity," "SKUs." Cross-check with IndiaMART — a genuine product company will have product listings with specs.

6. **Revenue Verification for Unlisted Companies:** Tofler operating revenue ranges (e.g., "Rs.100Cr-500Cr") are more reliable than RocketReach revenue estimates (which sometimes reflect USD revenue of parent or are outdated). For private companies, use Tofler as primary revenue source.

---

## 5. Tools and Code Used

No scraping code was written. Research was manual + AI-assisted:
- Claude (Anthropic) used for synthesis, scoring framework thinking, and drafting
- Web search for company-specific facts (all verified against primary sources)
- No automated data extraction; all criterion scores based on direct evidence from company websites, DSIR directories, Tofler, LinkedIn, and news sources

If I were to do this at scale, I would use:
- Python + BeautifulSoup for DSIR PDF parsing
- LinkedIn API (via PhantomBuster or Proxycurl) for founder background scraping
- Tofler API or screen-scraping for revenue band auto-classification

---

## 6. Yield Notes

- Started with ~80 named companies in Hyderabad biotech + specialty chemicals
- ~40 removed at first filter (too large, PE-owned, service company, government-owned)
- ~15 removed after deep research (borderline cases, unable to verify manufacturing status, stale websites)
- Final 25 includes 14 pass, 10 fail (with documented reasons), 1 borderline/watch list
- Yield of ~18% from initial universe matches the expected ~30% yield from the 75-100 that needed deep research, since the first 40 were eliminated quickly on hard filters

---

*Research conducted May 2026. Revenue figures reflect latest available data (FY24/FY25 where accessible).*
