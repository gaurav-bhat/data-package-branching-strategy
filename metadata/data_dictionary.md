# Data Dictionary

## Overview

This document provides detailed descriptions of all fields in the data package CSV files.

---

## 1. merge_conflict_metrics.csv

Records monthly merge conflict occurrences and their impact on development productivity.

| Field Name | Data Type | Unit | Description | Range/Values |
|------------|-----------|------|-------------|--------------|
| Month | String | YYYY-MM | Month of data collection | 2025-01 to 2025-12 |
| Period | String | Categorical | Study phase identifier | Baseline, Transition, Post-Implementation |
| Total_Merges | Integer | Count | Total number of merge operations performed | 0-1000 |
| Conflicts_Detected | Integer | Count | Number of merges that resulted in conflicts | 0-Total_Merges |
| Conflict_Rate_Percent | Float | Percentage | Percentage of merges with conflicts (Conflicts_Detected/Total_Merges × 100) | 0.00-100.00 |
| Avg_Resolution_Time_Hours | Float | Hours | Average time spent resolving each conflict | 0.0-24.0 |
| Developer_Hours_Lost | Float | Hours | Total developer time spent on conflict resolution (Conflicts_Detected × Avg_Resolution_Time_Hours) | 0.0-1000.0 |
| Team_Size | Integer | Count | Number of active developers during the month | 5-8 |

**Primary KPI:** Conflict_Rate_Percent demonstrates the 71.7% reduction in merge conflicts (42.4% → 12.0%, Cohen's d = 3.12, p < 0.001).

---

## 2. deployment_frequency_metrics.csv

Tracks deployment frequency, success rates, and reliability metrics.

| Field Name | Data Type | Unit | Description | Range/Values |
|------------|-----------|------|-------------|--------------|
| Month | String | YYYY-MM | Month of data collection | 2025-01 to 2025-12 |
| Period | String | Categorical | Study phase identifier | Baseline, Transition, Post-Implementation |
| Production_Deployments | Integer | Count | Number of scheduled production deployments | 0-100 |
| Hotfix_Deployments | Integer | Count | Number of emergency/hotfix deployments | 0-50 |
| Total_Deployments | Integer | Count | Sum of production and hotfix deployments (KPI basis — unchanged) | 0-150 |
| Feature_Dev_Deployments | Integer | Count | Feature-branch deployments to dev/sandbox environment (manually triggered by developers via GitLab CI; previously excluded, now included for full dataset transparency) | 0-50 |
| Total_All_Deployments | Integer | Count | Sum of all deployment events across all environments (Total_Deployments + Feature_Dev_Deployments); corresponds to the 214-event dataset cited in the manuscript | 0-200 |
| Avg_Days_Between_Deploys | Float | Days | Average number of days between deployments (30/Total_Deployments) | 0.0-30.0 |
| Failed_Deployments | Integer | Count | Number of deployments that failed | 0-Total_Deployments |
| Rollback_Count | Integer | Count | Number of deployments that required rollback | 0-Total_Deployments |
| Success_Rate_Percent | Float | Percentage | Percentage of successful deployments ((Total-Failed)/Total × 100) | 0.00-100.00 |

**Primary KPI:** Total_Deployments demonstrates the 181.0% increase in deployment frequency (6.3 → 17.7/month, Cohen's d = 2.85, p < 0.001). Feature-branch dev-environment deployments were previously excluded from this dataset; they are now included in the `Feature_Dev_Deployments` column. `Total_Deployments` (production + hotfix) remains unchanged to preserve KPI integrity. The full 214-event dataset referenced in the manuscript equals the sum of `Total_All_Deployments` across all 12 months.

---

## 3. deployment_autonomy_metrics.csv

Measures the degree of automation and autonomy in the deployment process.

| Field Name | Data Type | Unit | Description | Range/Values |
|------------|-----------|------|-------------|--------------|
| Month | String | YYYY-MM | Month of data collection | 2025-01 to 2025-12 |
| Period | String | Categorical | Study phase identifier | Baseline, Transition, Post-Implementation |
| Total_Deployments | Integer | Count | Total number of deployment attempts | 0-100 |
| Autonomous_Deployments | Integer | Count | Deployments completed without manual approval | 0-Total_Deployments |
| Manual_Approval_Required | Integer | Count | Deployments requiring manual approval/intervention | 0-Total_Deployments |
| Deployment_Autonomy_Percent | Float | Percentage | Percentage of autonomous deployments (Autonomous/Total × 100) | 0.00-100.00 |
| Avg_Approval_Wait_Hours | Float | Hours | Average wait time for manual approvals | 0.0-48.0 |
| Total_Wait_Time_Hours | Float | Hours | Cumulative wait time for all manual approvals | 0.0-500.0 |
| CI_CD_Pipeline_Success_Rate | Float | Percentage | Percentage of CI/CD pipeline runs that succeeded | 0.00-100.00 |

**Primary KPI:** Avg_Approval_Wait_Hours demonstrates the 70.8% improvement in deployment autonomy (240m → 70m, Cohen's d = 2.44, p < 0.001). Deployment_Autonomy_Percent is a supporting metric showing the autonomy rate increase from 31.7% to 87.7%.

---

## 4. branch_lifecycle_metrics.csv

Tracks branch creation, lifecycle, and management patterns.

| Field Name | Data Type | Unit | Description | Range/Values |
|------------|-----------|------|-------------|--------------|
| Month | String | YYYY-MM | Month of data collection | 2025-01 to 2025-12 |
| Period | String | Categorical | Study phase identifier | Baseline, Transition, Post-Implementation |
| Active_Developers | Integer | Count | Number of developers actively committing code | 1-20 |
| Feature_Branches_Created | Integer | Count | Number of new feature branches created | 0-100 |
| Feature_Branches_Merged | Integer | Count | Number of feature branches successfully merged | 0-Feature_Branches_Created |
| Avg_Branch_Lifetime_Days | Float | Days | Average duration from branch creation to merge | 0.0-90.0 |
| Long_Lived_Branches_Count | Integer | Count | Branches existing longer than 14 days | 0-50 |
| Abandoned_Branches | Integer | Count | Branches created but never merged or deleted | 0-50 |
| Branch_Naming_Compliance_Percent | Float | Percentage | Percentage of branches following naming convention | 0.00-100.00 |

**Supporting Metric:** Demonstrates improved branch management and reduced technical debt.

---

## 5. code_review_metrics.csv

Captures code review quality, efficiency, and conflict detection during review phase.

| Field Name | Data Type | Unit | Description | Range/Values |
|------------|-----------|------|-------------|--------------|
| Month | String | YYYY-MM | Month of data collection | 2025-01 to 2025-12 |
| Period | String | Categorical | Study phase identifier | Baseline, Transition, Post-Implementation |
| Total_PRs | Integer | Count | Total pull requests opened | 0-200 |
| Avg_PR_Review_Time_Hours | Float | Hours | Average time from PR creation to approval | 0.0-100.0 |
| PRs_With_Conflicts | Integer | Count | Pull requests that had merge conflicts | 0-Total_PRs |
| PR_Conflict_Rate_Percent | Float | Percentage | Percentage of PRs with conflicts (PRs_With_Conflicts/Total_PRs × 100) | 0.00-100.00 |
| Avg_Review_Comments | Float | Count | Average number of review comments per PR | 0.0-50.0 |
| PRs_Requiring_Rework | Integer | Count | PRs that required significant changes after review | 0-Total_PRs |
| Rework_Rate_Percent | Float | Percentage | Percentage of PRs requiring rework | 0.00-100.00 |

**Supporting Metric:** Shows improved code review efficiency and reduced conflict rates during PR phase.

---

## 6. team_velocity_metrics.csv

Measures overall team productivity and delivery metrics.

| Field Name | Data Type | Unit | Description | Range/Values |
|------------|-----------|------|-------------|--------------|
| Month | String | YYYY-MM | Month of data collection | 2025-01 to 2025-12 |
| Period | String | Categorical | Study phase identifier | Baseline, Transition, Post-Implementation |
| Team_Size | Integer | Count | Number of team members | 1-20 |
| Completed_Features | Integer | Count | Number of features completed and deployed | 0-50 |
| Bug_Fix_Deployments | Integer | Count | Number of bug fix deployments | 0-30 |
| Avg_Feature_Completion_Days | Float | Days | Average days from feature start to production | 0.0-60.0 |
| Deployment_Lead_Time_Hours | Float | Hours | Average time from code commit to production deployment | 0.0-200.0 |
| MTTR_Minutes | Float | Minutes | Mean Time To Recovery for production incidents | 0.0-500.0 |
| Development_Velocity_Story_Points | Integer | Points | Total story points completed (using Fibonacci scale) | 0-200 |

**Supporting Metric:** Demonstrates overall team productivity improvements and faster time-to-market.

---

## Calculated Fields

Several fields are calculated from other fields. Here are the formulas:

### merge_conflict_metrics.csv
```
Conflict_Rate_Percent = (Conflicts_Detected / Total_Merges) × 100
Developer_Hours_Lost = Conflicts_Detected × Avg_Resolution_Time_Hours
```

### deployment_frequency_metrics.csv
```
Total_Deployments = Production_Deployments + Hotfix_Deployments
Avg_Days_Between_Deploys = 30 / Total_Deployments (approximate)
Success_Rate_Percent = ((Total_Deployments - Failed_Deployments) / Total_Deployments) × 100
```

### deployment_autonomy_metrics.csv
```
Total_Deployments = Autonomous_Deployments + Manual_Approval_Required
Deployment_Autonomy_Percent = (Autonomous_Deployments / Total_Deployments) × 100
Total_Wait_Time_Hours = Manual_Approval_Required × Avg_Approval_Wait_Hours
```

### code_review_metrics.csv
```
PR_Conflict_Rate_Percent = (PRs_With_Conflicts / Total_PRs) × 100
Rework_Rate_Percent = (PRs_Requiring_Rework / Total_PRs) × 100
```

---

## Data Quality Notes

1. **Precision:** Percentage values are rounded to 2 decimal places
2. **Time Measurements:** All time-based measurements were collected from automated systems with ±5 minute accuracy
3. **Missing Data:** No missing data in this dataset; all months have complete records
4. **Outliers:** No statistical outliers detected; all values within expected ranges
5. **Validation:** Data was cross-validated across Git logs, CI/CD systems, and manual audits

---

## Measurement Tools

- **Git Analysis:** Custom Python scripts using GitPython library
- **CI/CD Metrics:** Jenkins API and GitHub Actions API
- **Team Velocity:** Jira REST API
- **Aggregation:** Pandas data frames with monthly rollups

---

## Study Periods Definition

| Period | Months | Description |
|--------|--------|-------------|
| Baseline | 2025-01 to 2025-03 | Legacy branching strategy with centralized approval workflow |
| Transition | 2025-04 to 2025-06 | Implementation and learning phase of new branching strategy |
| Post-Implementation | 2025-07 to 2025-12 | Stabilized operation under new branching strategy with optimizations |

---

**Last Updated:** March 3, 2026  
**Version:** 1.0
