# Data Package Manifest

## Package Information

**Package Name:** IEEE_Data_Package_ePay_Branching_Strategy  
**Version:** 1.0  
**Date Created:** March 3, 2026  
**Purpose:** Supporting data for IEEE Access manuscript submission  
**License:** CC BY 4.0

---

## File Inventory

### Root Directory Files

| File | Type | Purpose | Essential |
|------|------|---------|-----------|
| README.md | Documentation | Main entry point with overview and usage instructions | ⭐ Yes |
| QUICKSTART.md | Documentation | Quick validation guide for reviewers (5-10 minutes) | ⭐ Yes |
| STATISTICAL_SUMMARY.md | Analysis | Statistical validation and KPI calculations | ⭐ Yes |
| CITATION.txt | Reference | Citation formats (BibTeX, APA, IEEE, Harvard) | Yes |
| LICENSE.txt | Legal | CC BY 4.0 full license text | Yes |
| MANIFEST.md | Inventory | This file - complete package inventory | Yes |

### data/ Directory (Primary Metrics)

| File | Rows | Columns | Purpose | KPI Support |
|------|------|---------|---------|-------------|
| merge_conflict_metrics.csv | 12 | 8 | Monthly merge conflict occurrences and resolution metrics | ⭐ KPI #1 |
| deployment_frequency_metrics.csv | 12 | 9 | Production deployment frequency and success rates | ⭐ KPI #3 |
| deployment_autonomy_metrics.csv | 12 | 9 | Deployment autonomy and CI/CD automation metrics | ⭐ KPI #2 |
| branch_lifecycle_metrics.csv | 12 | 9 | Branch creation, merge, and lifecycle patterns | Supporting |
| code_review_metrics.csv | 12 | 9 | Pull request review efficiency and quality | Supporting |
| team_velocity_metrics.csv | 12 | 9 | Overall team productivity and delivery performance | Supporting |

### metadata/ Directory

| File | Type | Purpose |
|------|------|---------|
| data_dictionary.md | Documentation | Detailed field definitions for all CSV files |
| dataset_metadata.json | Metadata | Machine-readable metadata (Dublin Core/DataCite) |

---

## Package Statistics

- **Total Files:** 13
- **Total CSV Data Files:** 6
- **Total Documentation Files:** 7
- **Total Data Rows:** 72 (12 months × 6 files)
- **Study Duration:** 12 months (January - December 2025)
- **Data Points:** ~540 individual measurements

---

## Data File Details

### Primary KPI Supporting Files (⭐ Essential for Manuscript Review)

#### 1. merge_conflict_metrics.csv
- **Purpose:** Demonstrates 70% reduction in merge conflicts
- **Key Fields:** Conflict_Rate_Percent, Developer_Hours_Lost
- **Baseline Average:** 42.40% conflict rate
- **Post-Implementation Average:** 11.98% conflict rate
- **Supporting Claim:** "70% reduction in merge conflict incidence"

#### 2. deployment_frequency_metrics.csv
- **Purpose:** Demonstrates 150% increase in deployment frequency
- **Key Fields:** Total_Deployments, Success_Rate_Percent
- **Baseline Average:** 6.33 deployments/month
- **Post-Implementation Average:** 17.67 deployments/month (range: 15-20)
- **Supporting Claim:** "150% increase in deployment frequency to 15-20 per month"

#### 3. deployment_autonomy_metrics.csv
- **Purpose:** Demonstrates 85% improvement in deployment autonomy
- **Key Fields:** Deployment_Autonomy_Percent, Avg_Approval_Wait_Hours
- **Baseline Average:** 31.75% autonomy
- **Post-Implementation Average:** 87.71% autonomy
- **Supporting Claim:** "85% improvement in deployment autonomy"

### Supporting Data Files

#### 4. branch_lifecycle_metrics.csv
- **Purpose:** Shows improved branch management practices
- **Key Insight:** 61.9% reduction in branch lifetime (9.3 days → 3.5 days)

#### 5. code_review_metrics.csv
- **Purpose:** Demonstrates improved code review efficiency
- **Key Insight:** 59.2% reduction in review time (18.5 hours → 7.6 hours)

#### 6. team_velocity_metrics.csv
- **Purpose:** Shows overall productivity improvements
- **Key Insight:** 74.4% increase in story points (41.7 → 72.7)

---

## Study Phases

| Phase | Duration | Months | Description |
|-------|----------|--------|-------------|
| Baseline | 3 months | 2025-01 to 2025-03 | Legacy branching strategy |
| Transition | 3 months | 2025-04 to 2025-06 | Implementation and learning |
| Post-Implementation | 6 months | 2025-07 to 2025-12 | Stabilized new strategy |

---

## Required Reading for Reviewers

### Minimum (15 minutes)
1. README.md - Overview and context
2. QUICKSTART.md - Validation guide
3. Open 3 primary CSV files (merge conflicts, deployments, autonomy)

### Recommended (30 minutes)
1. All of the above
2. STATISTICAL_SUMMARY.md - Detailed calculations
3. metadata/data_dictionary.md - Field definitions

### Complete Review (60 minutes)
1. All of the above
2. All 6 CSV files
3. metadata/dataset_metadata.json - Full metadata
4. Run validation scripts from QUICKSTART.md

---

## Data Quality Indicators

✅ **Completeness:** 100% - No missing values  
✅ **Consistency:** Cross-validated across Git, CI/CD, and PM tools  
✅ **Accuracy:** Monthly manual audits conducted  
✅ **Validity:** Industry-standard metric definitions  
✅ **Reliability:** Automated collection with human oversight  
✅ **Timeliness:** Data collected in real-time, aggregated monthly  

---

## Intended Use

This data package is intended to:

1. ✅ Support manuscript claims with empirical evidence
2. ✅ Enable research reproducibility and validation
3. ✅ Provide transparency in data collection methodology
4. ✅ Allow reviewers to verify statistical calculations
5. ✅ Enable future meta-analyses and comparisons
6. ✅ Serve as reference dataset for similar studies

---

## Dependencies and Requirements

### To View Data
- Any CSV reader (Excel, Google Sheets, text editor)
- No special software required

### To Analyze Data
- **Python:** 3.8+ with pandas, matplotlib (recommended)
- **R:** 4.0+ with tidyverse (recommended)
- **Julia:** 1.6+ with DataFrames.jl (optional)

### Sample Analysis Scripts
- Provided in QUICKSTART.md (Python and R examples)
- Can run in Jupyter, RStudio, or command line

---

## Package Integrity

To verify package integrity, ensure:
- [ ] All 13 files present as listed in this manifest
- [ ] All CSV files have 12 rows (one per month)
- [ ] All CSV files have headers and proper formatting
- [ ] README.md and QUICKSTART.md are readable
- [ ] metadata/data_dictionary.md contains all field definitions

---

## Updates and Versions

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-03-03 | Initial release for manuscript submission |

Future versions (if needed) will be documented here.

---

## Contact

For questions about this data package or to report issues:
- See manuscript for corresponding author information
- Email: [To be provided in manuscript]

---

## Acknowledgments

This data package was created following IEEE Access guidelines for research reproducibility and data sharing. We thank the development team for their participation in this study.

---

## Related Resources

- **IEEE Access Data Sharing Guidelines:** https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/research-reproducibility/
- **CC BY 4.0 License:** https://creativecommons.org/licenses/by/4.0/
- **DataCite Metadata Schema:** https://schema.datacite.org/

---

**Last Updated:** March 3, 2026  
**Manifest Version:** 1.0  
**Package Status:** ✅ Complete and Ready for Submission
