# Quick Start Guide for Reviewers

## Purpose

This guide helps manuscript reviewers and researchers quickly understand, validate, and analyze the data package in 5-10 minutes.

---

## ⚡ 5-Minute Overview

### What's in This Package?

**Primary Goal:** Empirical validation of branching strategy improvements in production payment system

**Study Duration:** 12 months (Jan-Dec 2025)  
**Team Size:** 5-8 developers  
**System:** Enterprise payment processing (24/7 production)

### Three Main Claims

1. ✅ **71.7% reduction** in merge conflicts → See `merge_conflict_metrics.csv`
2. ✅ **70.8% improvement** in deployment autonomy (Approval Wait Time: 240m → 70m) → See `deployment_autonomy_metrics.csv`
3. ✅ **181.0% increase** in deployment frequency (6.3 → 17.7/month) → See `deployment_frequency_metrics.csv`

---

## 📁 File Structure

```
IEEE_Data_Package_Pay_Branching_Strategy/
├── README.md                          ← Start here
├── STATISTICAL_SUMMARY.md             ← Validation calculations
├── CITATION.txt                       ← How to cite
├── QUICKSTART.md                      ← This file
├── data/
│   ├── merge_conflict_metrics.csv     ← KPI #1 data
│   ├── deployment_frequency_metrics.csv   ← KPI #3 data
│   ├── deployment_autonomy_metrics.csv    ← KPI #2 data
│   ├── branch_lifecycle_metrics.csv       ← Supporting data
│   ├── code_review_metrics.csv            ← Supporting data
│   └── team_velocity_metrics.csv          ← Supporting data
└── metadata/
    ├── data_dictionary.md             ← Field definitions
    └── dataset_metadata.json          ← Machine-readable metadata
```

---

## 🔍 Quick Validation (3 Steps)

### Step 1: Verify KPI #1 (Merge Conflicts)

```bash
# Open merge_conflict_metrics.csv
# Compare: Baseline (rows 1-3) vs Post-Implementation (rows 7-12)
```

**Expected:**
- Baseline average: ~42.4% conflict rate
- Post-implementation: ~12.0% conflict rate
- Reduction: ~71.7% ✓

### Step 2: Verify KPI #2 (Deployment Autonomy)

```bash
# Open deployment_autonomy_metrics.csv
# Compare: Avg_Approval_Wait_Hours column (primary KPI metric)
```

**Expected:**
- Baseline average AWT: ~240 min (4.0 hours)
- Post-implementation AWT: ~70 min (1.17 hours)
- Improvement: 70.8% reduction in wait time ✓
- Supporting metric: Autonomy rate rises from ~31.7% to ~87.7%

### Step 3: Verify KPI #3 (Deployment Frequency)

```bash
# Open deployment_frequency_metrics.csv
# Compare: Total_Deployments column
```

**Expected:**
- Baseline average: ~6.3 deployments/month
- Post-implementation: ~17.7 deployments/month
- Increase: 181.0% ✓ (based on 214 total deployment events)

---

## 💻 Load Data in Python (30 seconds)

```python
import pandas as pd

# Load all CSV files
conflicts = pd.read_csv('data/merge_conflict_metrics.csv')
deployments = pd.read_csv('data/deployment_frequency_metrics.csv')
autonomy = pd.read_csv('data/deployment_autonomy_metrics.csv')

# Quick validation
print("KPI #1 - Conflict Rate Reduction:")
baseline = conflicts[conflicts['Period']=='Baseline']['Conflict_Rate_Percent'].mean()
post = conflicts[conflicts['Period']=='Post-Implementation']['Conflict_Rate_Percent'].mean()
print(f"  Baseline: {baseline:.2f}%")
print(f"  Post-Impl: {post:.2f}%")
print(f"  Reduction: {((baseline-post)/baseline*100):.1f}%\n")

print("KPI #2 - Deployment Autonomy (Approval Wait Time Reduction):")
baseline = autonomy[autonomy['Period']=='Baseline']['Avg_Approval_Wait_Hours'].mean() * 60  # convert to min
post = autonomy[autonomy['Period']=='Post-Implementation']['Avg_Approval_Wait_Hours'].mean() * 60
print(f"  Baseline AWT: {baseline:.0f} min")
print(f"  Post-Impl AWT: {post:.0f} min")
print(f"  Reduction: {((baseline-post)/baseline*100):.1f}%\n")

print("KPI #3 - Deployment Frequency Increase:")
baseline = deployments[deployments['Period']=='Baseline']['Total_Deployments'].mean()
post = deployments[deployments['Period']=='Post-Implementation']['Total_Deployments'].mean()
print(f"  Baseline: {baseline:.1f} deployments/month")
print(f"  Post-Impl: {post:.1f} deployments/month")
print(f"  Increase: {((post-baseline)/baseline*100):.1f}%")
```

---

## 📊 Quick Visualization

```python
import matplotlib.pyplot as plt

# Plot merge conflict trends
fig, axes = plt.subplots(1, 3, figsize=(15, 4))

# Conflict Rate
axes[0].plot(conflicts['Month'], conflicts['Conflict_Rate_Percent'], marker='o')
axes[0].axhline(y=42.4, color='r', linestyle='--', label='Baseline Avg')
axes[0].axhline(y=12.0, color='g', linestyle='--', label='Post-Impl Avg')
axes[0].set_title('Merge Conflict Rate')
axes[0].set_ylabel('Conflict Rate (%)')
axes[0].legend()
axes[0].tick_params(axis='x', rotation=45)

# Deployment Frequency
axes[1].plot(deployments['Month'], deployments['Total_Deployments'], marker='o')
axes[1].axhline(y=6.3, color='r', linestyle='--', label='Baseline Avg')
axes[1].axhline(y=17.7, color='g', linestyle='--', label='Post-Impl Avg')
axes[1].set_title('Deployment Frequency')
axes[1].set_ylabel('Deployments/Month')
axes[1].legend()
axes[1].tick_params(axis='x', rotation=45)

# Approval Wait Time (KPI #2)
axes[2].plot(autonomy['Month'], autonomy['Avg_Approval_Wait_Hours'].apply(lambda x: x*60), marker='o')
axes[2].axhline(y=240, color='r', linestyle='--', label='Baseline Avg (240m)')
axes[2].axhline(y=70, color='g', linestyle='--', label='Post-Impl Avg (70m)')
axes[2].set_title('Approval Wait Time (AWT)')
axes[2].set_ylabel('Wait Time (min)')
axes[2].legend()
axes[2].tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.savefig('kpi_validation.png', dpi=300, bbox_inches='tight')
plt.show()

print("✅ Visualization saved as 'kpi_validation.png'")
```

---

## 📈 Load Data in R

```r
library(tidyverse)

# Load data
conflicts <- read_csv('data/merge_conflict_metrics.csv')
deployments <- read_csv('data/deployment_frequency_metrics.csv')
autonomy <- read_csv('data/deployment_autonomy_metrics.csv')

# Quick validation
conflicts %>%
  group_by(Period) %>%
  summarise(avg_conflict_rate = mean(Conflict_Rate_Percent))

deployments %>%
  group_by(Period) %>%
  summarise(avg_deployments = mean(Total_Deployments))

autonomy %>%
  group_by(Period) %>%
  summarise(avg_autonomy = mean(Deployment_Autonomy_Percent))
```

---

## ✅ Validation Checklist for Reviewers

- [ ] All three CSV files load without errors
- [ ] 12 rows of data in each primary metric file (one per month)
- [ ] Baseline period shows expected lower performance
- [ ] Post-implementation period shows sustained improvement
- [ ] No missing values or anomalies
- [ ] KPI #1: Conflict rate drops from ~42.4% to ~12.0% (71.7% reduction, Cohen's d=3.12)
- [ ] KPI #2: Approval Wait Time drops from ~240m to ~70m (70.8% reduction, Cohen's d=2.44)
- [ ] KPI #3: Deployments increase from ~6.3 to ~17.7 per month (181.0% increase, Cohen's d=2.85)
- [ ] Statistical summary shows p < 0.001 for all KPIs
- [ ] Metadata files are complete and accurate

---

## 📚 Additional Resources

- **Detailed explanations:** See `README.md`
- **Field definitions:** See `metadata/data_dictionary.md`
- **Statistical validation:** See `STATISTICAL_SUMMARY.md`
- **Dataset metadata:** See `metadata/dataset_metadata.json`

---

## 🤔 Common Questions

### Q: Why only 12 months of data?
**A:** Standard empirical study duration; includes 3-month baseline, 3-month transition, and 6-month stabilization period.

### Q: How was data collected?
**A:** Automated collection from Git (GitPython), CI/CD (GitLab CI/CD — 214 deployment events), and project management (Jira REST API). Monthly manual validation.

### Q: Are there any missing data points?
**A:** No. All 12 months have complete data for all metrics.

### Q: What about statistical significance?
**A:** All three KPIs show p < 0.001 with large to very large effect sizes (Cohen's d: 3.12, 2.44, 2.85). Cross-verified with Mann-Whitney U test. See STATISTICAL_SUMMARY.md.

### Q: Can I reproduce the analysis?
**A:** Yes! Sample Python code is provided in this guide and README.md. All data is in standard CSV format.

---

## 📞 Contact

For questions about this data package:
- See manuscript for author contact information
- Review comments can be addressed through IEEE Access review system

---

## ⏱️ Time Investment

- **5-minute scan:** This guide + open 3 main CSV files
- **15-minute review:** Load data in Python/R + run validation script
- **30-minute deep dive:** Statistical summary + data dictionary + full visualization
- **1-hour analysis:** Reproduce all calculations + generate custom visualizations

---

**Last Updated:** March 3, 2026  
**Version:** 1.0  
**Reviewer Friendly:** ⭐⭐⭐⭐⭐
