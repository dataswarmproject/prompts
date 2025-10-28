# Data Analysis Prompts

Professional prompts for data analysts, data scientists, and business intelligence professionals.

## Categories

1. [Data Exploration](#data-exploration)
2. [Statistical Analysis](#statistical-analysis)
3. [Data Visualization](#data-visualization)
4. [Machine Learning](#machine-learning)
5. [SQL & Database](#sql-and-database)
6. [Reporting](#reporting)

---

## Data Exploration

### Initial Data Analysis

```
Analyze this dataset and provide comprehensive insights:

Dataset: [name/description]
Source: [where data comes from]
Size: [rows x columns]

Data preview:
```
[First few rows or data description]
```

Column descriptions:
- [column1]: [type, description]
- [column2]: [type, description]
...

Please provide:
1. Data quality assessment:
   - Missing values analysis
   - Duplicate records
   - Data type issues
   - Outliers and anomalies

2. Descriptive statistics:
   - Central tendency measures
   - Dispersion measures
   - Distribution shapes

3. Correlation analysis:
   - Key relationships between variables
   - Potential multicollinearity

4. Initial insights and patterns

5. Recommended next steps for analysis

6. Python/R code for this exploration

Format: Clear sections with visualizations described
```

### Data Cleaning Strategy

```
Create a data cleaning strategy for this messy dataset:

Current issues:
- [Issue 1: e.g., 30% missing values in key column]
- [Issue 2: e.g., inconsistent date formats]
- [Issue 3: e.g., outliers in numeric fields]
- [Issue 4: e.g., duplicate records]

Dataset context:
- Purpose: [what analysis will be done]
- Critical fields: [fields that must be clean]
- Acceptable data loss: [percentage]

Provide:
1. Step-by-step cleaning plan
2. Decision rules for each issue:
   - Missing values: impute/drop/flag?
   - Outliers: remove/cap/transform?
   - Duplicates: merge/remove/keep?
3. Python/R code for implementation
4. Data quality checks post-cleaning
5. Documentation of changes made

Goal: Clean, reliable dataset ready for analysis
```

---

## Statistical Analysis

### Hypothesis Testing

```
Design and conduct a statistical test for:

Research question: [your question]

Data:
- Sample size: [n]
- Variables: [list variables and types]
- Groups: [if applicable]

Context:
- [Business context]
- [Why this matters]

Please provide:
1. Null and alternative hypotheses
2. Appropriate statistical test (with justification)
3. Assumptions to check (and how to check them)
4. Significance level (alpha)
5. Test implementation code (Python/R)
6. Results interpretation:
   - Test statistic
   - P-value
   - Confidence interval
   - Effect size
7. Business implications
8. Limitations and caveats

Format: Clear narrative with code and visualizations
```

### A/B Test Analysis

```
Analyze this A/B test:

Test setup:
- Control group: [description, sample size]
- Treatment group: [description, sample size]
- Metric: [primary metric]
- Duration: [test length]

Data:
```
[Provide summary statistics or data]
```

Business context:
- [What was changed]
- [Why we tested this]
- [Decision threshold]

Analyze:
1. Sample size and power analysis
2. Group balance check
3. Statistical significance test
4. Practical significance (effect size)
5. Confidence intervals
6. Segment analysis (if relevant):
   - [Segment 1]
   - [Segment 2]
7. Recommendations:
   - Ship it?
   - Iterate?
   - Kill it?
8. Next experiments to run

Include code and visualizations
```

---

## Data Visualization

### Dashboard Design

```
Design a dashboard for [purpose]

Audience: [who will use this]
Decision: [what decision does this support]
Update frequency: [real-time/daily/weekly]

Key metrics to display:
1. [Metric 1]: [why important]
2. [Metric 2]: [why important]
3. [Metric 3]: [why important]

Data sources:
- [Source 1]
- [Source 2]

Please provide:
1. Dashboard layout (describe sections)
2. For each visualization:
   - Chart type (with justification)
   - Metrics displayed
   - Filters/interactivity
   - Color scheme (with accessibility)
3. KPI card designs
4. Drill-down paths
5. Alert/threshold settings
6. Implementation plan:
   - Tool: [Tableau/PowerBI/Python/etc.]
   - Refresh schedule
   - Access controls

Guiding principles:
- Information hierarchy
- Minimize cognitive load
- Actionable insights
- Mobile responsive if needed
```

### Chart Selection

```
Recommend the best visualization for this data:

Data description:
- Type: [time series/categorical/continuous/etc.]
- Variables: [list variables]
- Relationship to show: [comparison/distribution/trend/etc.]
- Sample size: [n]

Purpose: [what insight to communicate]
Audience: [technical/executive/general]

Provide:
1. Recommended chart type (with rationale)
2. Alternative options (pros/cons)
3. Design specifications:
   - Axes labels
   - Color scheme
   - Annotations needed
   - Title and subtitle
4. Python/R code to generate
5. Common mistakes to avoid
6. Accessibility considerations

Show example with sample data
```

---

## Machine Learning

### Model Selection

```
Recommend ML approach for this problem:

Problem: [describe prediction/classification task]
Business goal: [what success looks like]

Data:
- Target variable: [variable, type]
- Features: [list key features]
- Sample size: [training data size]
- Balance: [class distribution if classification]
- Data quality: [any issues]

Constraints:
- Interpretability needs: [black box ok or need explainability]
- Latency requirements: [real-time or batch]
- Accuracy requirements: [minimum acceptable]
- Resources: [compute, time available]

Provide:
1. Recommended algorithm(s) with justification
2. Feature engineering suggestions
3. Train/validation/test split strategy
4. Evaluation metrics to use
5. Baseline model to beat
6. Implementation outline (Python/R/framework)
7. Expected performance range
8. Risks and mitigation strategies

Include code skeleton for recommended approach
```

### Model Evaluation

```
Evaluate this machine learning model:

Model type: [algorithm]
Task: [classification/regression/clustering]

Performance metrics:
```
[Provide metrics: accuracy, precision, recall, RMSE, etc.]
```

Context:
- Training data: [size, description]
- Test data: [size, description]
- Business baseline: [current performance without ML]

Analyze:
1. Overall performance assessment
2. Overfitting/underfitting check
3. Confusion matrix analysis (if classification)
4. Feature importance
5. Error analysis:
   - Where model fails
   - Why it fails
   - Examples of errors
6. Comparison to baseline
7. Production readiness:
   - Performance threshold met?
   - Bias/fairness check
   - Robustness to edge cases
8. Recommendations:
   - Deploy as-is?
   - Improve first (how)?
   - Collect more data?

Provide improvement action plan if needed
```

---

## SQL and Database

### SQL Query Optimization

```
Optimize this SQL query:

Current query:
```sql
[Your query]
```

Performance issues:
- Current execution time: [time]
- Target execution time: [goal]
- Problem: [slow/memory intensive/etc.]

Database context:
- DBMS: [PostgreSQL/MySQL/SQL Server/etc.]
- Table sizes: [row counts]
- Current indexes: [list indexes]
- Query frequency: [how often run]

Schema:
```sql
[Relevant table schemas]
```

Provide:
1. Query execution plan analysis
2. Bottleneck identification
3. Optimized query version(s)
4. Index recommendations
5. Alternative query approaches
6. Expected performance improvement
7. Trade-offs of optimization
8. Monitoring queries for production

Explain each optimization clearly
```

### Data Model Design

```
Design a database schema for [application/use case]

Requirements:
- Entities: [main entities to store]
- Relationships: [key relationships]
- Scale: [expected data volume]
- Query patterns: [common queries]

Data characteristics:
- Write frequency: [high/medium/low]
- Read frequency: [high/medium/low]
- Consistency needs: [strong/eventual]
- Growth rate: [data growth estimate]

Provide:
1. Entity-relationship diagram (text-based or Mermaid)
2. Table schemas with:
   - Column names and types
   - Primary keys
   - Foreign keys
   - Constraints
3. Indexing strategy
4. Normalization level (and justification)
5. Partitioning strategy if needed
6. Sample queries for common operations
7. Migration considerations
8. Scalability plan

Database type: [SQL/NoSQL/hybrid]
```

---

## Reporting

### Executive Summary

```
Create an executive summary for this analysis:

Analysis performed:
[Describe the analysis, methods used]

Key findings:
1. [Finding 1]
2. [Finding 2]
3. [Finding 3]

Data:
- Source: [source]
- Period: [time period]
- Sample size: [n]

Target audience: [C-level/Directors/Managers]
Purpose: [inform/recommend/alert]

Format:
1. Executive Summary (200 words max):
   - Business question
   - Key findings
   - Primary recommendation
   - Impact estimate

2. Visual Summary:
   - 1-3 key charts (describe)
   - One-slide summary

3. Recommendations:
   - Action 1 (priority, effort, impact)
   - Action 2 (priority, effort, impact)
   - Action 3 (priority, effort, impact)

4. Next Steps

Style: Clear, concise, business-focused (not technical)
Include: Confidence levels, limitations, assumptions
```

### Data Story

```
Turn this analysis into a compelling data story:

Analysis: [what you analyzed]

Data points:
- [Metric 1]: [value]
- [Metric 2]: [value]
- [Insight 1]: [description]
- [Insight 2]: [description]

Business context:
- [Why this matters]
- [Stakes involved]

Create a narrative with:
1. Hook (attention-grabbing opener)
2. Context (why we looked at this)
3. Journey (what we found, step by step)
4. Insight (the "aha" moment)
5. Implication (what it means)
6. Action (what to do now)

Storytelling elements:
- Use analogy or metaphor where appropriate
- Make data relatable (context, comparisons)
- Build tension and resolution
- Clear cause and effect
- Visuals to support story (describe)

Audience: [who will read this]
Length: [presentation/report/one-pager]
Tone: [data-driven but accessible]
```

---

## Quick Tips

1. **Context is Key**: Always explain what business problem you're solving
2. **Show Your Data**: Provide sample data or detailed descriptions
3. **Specify Tools**: Mention your preferred tools (Python/R/SQL/Excel)
4. **Define Success**: What does a good result look like?
5. **Ask for Code**: Request implementation code with explanations
6. **Request Visualizations**: Ask for chart descriptions or code

---

**See Also**:
- [AI Best Practices](../../AI-BEST-PRACTICES.md)
- [Researcher's Quick Start Guide](../../guides/researchers.md)
- [Python Data Analysis Template](./python-template.md)

**Last Updated**: 2025-10-28
