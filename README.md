# Data Package: A Policy-Driven Branching and Environment Isolation Strategy for Enterprise DevSecOps: An Empirical Industrial Case Study

## Overview

This data package supports the manuscript submitted to IEEE Access titled "A Policy-Driven Branching and Environment Isolation Strategy for Enterprise DevSecOps: An Empirical Industrial Case Study.

**Study Period:** January 2025 - December 2025 (12 months)  
**System:** Pay Portal - Enterprise Payment Processing System  
**Team Size:** 5-8 developers  
**Data Collection Method:** Automated metrics from Git, CI/CD pipelines, and project management tools

## Key Performance Indicators (KPIs)

This data package provides empirical evidence for the following key findings:

1. **71.7% Reduction in Merge Conflict Incidence**
   - Baseline conflict rate: ~42.4%
   - Post-implementation conflict rate: ~12.0%
   - Reduction: 71.7%

2. **70.8% Improvement in Deployment Autonomy**
   - Measured by Average Approval Wait Time (AWT) reduction
   - Baseline AWT: ~240 min (4.0 hours)
   - Post-implementation AWT: ~70 min (1.17 hours)
   - Improvement: 70.8% (recovering ~580 engineering hours annually)

3. **181.0% Increase in Deployment Frequency**
   - Baseline: ~6.3 deployments/month
   - Post-implementation: ~17.7 deployments/month
   - Increase: 181.0%

## Data Files

### Primary Metrics

1. **merge_conflict_metrics.csv**
   - Monthly merge conflict data
   - Tracks conflict rate, resolution time, and developer productivity impact
   - Directly supports KPI #1

2. **deployment_frequency_metrics.csv**
   - Production deployment frequency and success rates
   - Tracks deployment cadence, failures, and rollbacks
   - Directly supports KPI #3

3. **deployment_autonomy_metrics.csv**
   - Autonomous vs manual deployment tracking
   - CI/CD pipeline success rates and Average Approval Wait Time (AWT)
   - Directly supports KPI #2 (AWT reduction: 240m → 70m, 70.8% improvement)

### Supplementary Metrics

4. **branch_lifecycle_metrics.csv**
   - Branch creation, merge, and abandonment patterns
   - Branch lifetime duration and compliance metrics

5. **code_review_metrics.csv**
   - Pull request review times and conflict rates
   - Rework rates and review quality indicators

6. **team_velocity_metrics.csv**
   - Feature completion rates and development velocity
   - Deployment lead time and MTTR (Mean Time To Recovery)

## Study Methodology

### Data Collection

- **Git Repository Analysis:** Automated scripts analyzed commit history, branch patterns, and merge conflict occurrences
- **CI/CD Pipeline Logs:** GitLab CI/CD pipeline logs (214 deployment events) provided deployment frequency, success rates, and approval workflows
- **Project Management Tools:** Jira/Linear tracked feature completion, story points, and team velocity
- **Manual Validation:** Monthly reviews verified automated data collection accuracy

### Study Phases

1. **Baseline Period (Months 1-3):** Legacy branching strategy with centralized approval
2. **Transition Period (Months 4-6):** Implementation of new branching strategy with gradual rollout
3. **Post-Implementation Period (Months 7-12):** Stabilized new strategy with optimization

### Team Context

- Enterprise payment processing system in production
- Team grew from 5 to 8 developers during study
- 24/7 production system with PCI-DSS compliance requirements
- Multiple deployment environments (dev, staging, production)

## Data Format

All data files are in CSV format with the following conventions:

- **Date Format:** YYYY-MM (e.g., 2025-01)
- **Decimal Separator:** Period (.)
- **Encoding:** UTF-8
- **Missing Values:** Empty cells or "N/A"
- **Calculated Fields:** Percentages are stored as decimal values (e.g., 42.86 for 42.86%)

## Data Dictionary

See `metadata/data_dictionary.md` for detailed field descriptions.

## Reproducibility

### Prerequisites

To reproduce analysis from this data:
- Python 3.8+ or R 4.0+
- pandas/tidyverse for data manipulation
- matplotlib/ggplot2 for visualization

### Example Analysis

```python
import pandas as pd
import matplotlib.pyplot as plt

# Load merge conflict data
df = pd.read_csv('data/merge_conflict_metrics.csv')

# Calculate baseline vs post-implementation averages
baseline = df[df['Period'] == 'Baseline']['Conflict_Rate_Percent'].mean()
post_impl = df[df['Period'] == 'Post-Implementation']['Conflict_Rate_Percent'].mean()

print(f"Reduction: {((baseline - post_impl) / baseline * 100):.1f}%")
```

## Ethics and Compliance

- All data has been anonymized and aggregated
- No personally identifiable information (PII) is included
- Team members provided informed consent for data collection
- Data collection complied with organizational policies

## Data Availability Statement

This dataset is made available to support research reproducibility for the submitted manuscript. The data is provided under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.

## Contact Information

For questions about this data package, please contact:
- **Corresponding Author:** Gaurav B.
- **Email:** gaurav.bhat@gmail.com
- **Institution/Organization:** Open Text Corporation

## Citation

If you use this dataset, please cite:

```bibtex
@article{bhatnagar2026branching,
  title={A Policy-Driven Branching and Environment Isolation Strategy for Enterprise DevSecOps: An Empirical Industrial Case Study},
  author={Gaurav Bhatnagar},
  journal={IEEE Access},
  year={2026},
  doi={10.1109/ACCESS.2026.0429000},
  publisher={IEEE}
}
```

## Version History

- **v1.0** (March 2026): Initial release accompanying manuscript submission

## Acknowledgments

We thank the development team members who participated in this study and the organization for supporting this research.

---

**Last Updated:** March 3, 2026  
**Dataset Version:** v1.0.1-ieee-access-submission  
**Dataset DOI:** 10.5281/zenodo.18860898

