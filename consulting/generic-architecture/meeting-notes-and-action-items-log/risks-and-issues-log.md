# Risks and Issues Log Template

## Template Usage Instructions

This template helps AI systems create and maintain risks and issues logs:
- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project needs

## 1. Log Overview

### 1.1 Basic Information
<prompt: What are the fundamental details of this log?>
- Project Name: {{project_name}}
- Log Owner: {{log_owner}}
- Last Updated: {{last_updated}}
- Review Frequency: {{review_frequency}}

### 1.2 Purpose
<prompt: What is the purpose of tracking these risks and issues?>
- Primary Purpose: {{primary_purpose}}
- Tracking Scope: {{tracking_scope}}
- Success Criteria: {{success_criteria}}

## 2. Active Risks

### 2.1 High Impact Risks
<prompt: What are the high impact risks?>
{{for_each_high_risk}}
- Risk ID: {{risk_id}}
  - Description: {{risk_description}}
  - Impact Level: {{impact_level}}
  - Probability: {{probability}}
  - Severity: {{severity_rating}}
  - Category: {{risk_category}}
  - Mitigation Strategy: {{mitigation_strategy}}
  - Owner: {{risk_owner}}
  - Status: {{current_status}}
  - Monitoring Plan: {{monitoring_approach}}
{{end_for_each}}

### 2.2 Medium Impact Risks
<prompt: What are the medium impact risks?>
{{for_each_medium_risk}}
- Risk ID: {{risk_id}}
  - Description: {{risk_description}}
  - Impact Level: {{impact_level}}
  - Probability: {{probability}}
  - Severity: {{severity_rating}}
  - Category: {{risk_category}}
  - Mitigation Strategy: {{mitigation_strategy}}
  - Owner: {{risk_owner}}
  - Status: {{current_status}}
  - Monitoring Plan: {{monitoring_approach}}
{{end_for_each}}

### 2.3 Low Impact Risks
<prompt: What are the low impact risks?>
{{for_each_low_risk}}
- Risk ID: {{risk_id}}
  - Description: {{risk_description}}
  - Impact Level: {{impact_level}}
  - Probability: {{probability}}
  - Severity: {{severity_rating}}
  - Category: {{risk_category}}
  - Mitigation Strategy: {{mitigation_strategy}}
  - Owner: {{risk_owner}}
  - Status: {{current_status}}
  - Monitoring Plan: {{monitoring_approach}}
{{end_for_each}}

## 3. Active Issues

### 3.1 High Priority Issues
<prompt: What are the high priority issues?>
{{for_each_high_priority_issue}}
- Issue ID: {{issue_id}}
  - Description: {{issue_description}}
  - Impact: {{impact_level}}
  - Priority: {{priority_level}}
  - Category: {{issue_category}}
  - Resolution Plan: {{resolution_plan}}
  - Owner: {{issue_owner}}
  - Target Date: {{target_resolution_date}}
  - Status: {{current_status}}
  - Progress: {{progress_notes}}
{{end_for_each}}

### 3.2 Medium Priority Issues
<prompt: What are the medium priority issues?>
{{for_each_medium_priority_issue}}
- Issue ID: {{issue_id}}
  - Description: {{issue_description}}
  - Impact: {{impact_level}}
  - Priority: {{priority_level}}
  - Category: {{issue_category}}
  - Resolution Plan: {{resolution_plan}}
  - Owner: {{issue_owner}}
  - Target Date: {{target_resolution_date}}
  - Status: {{current_status}}
  - Progress: {{progress_notes}}
{{end_for_each}}

### 3.3 Low Priority Issues
<prompt: What are the low priority issues?>
{{for_each_low_priority_issue}}
- Issue ID: {{issue_id}}
  - Description: {{issue_description}}
  - Impact: {{impact_level}}
  - Priority: {{priority_level}}
  - Category: {{issue_category}}
  - Resolution Plan: {{resolution_plan}}
  - Owner: {{issue_owner}}
  - Target Date: {{target_resolution_date}}
  - Status: {{current_status}}
  - Progress: {{progress_notes}}
{{end_for_each}}

## 4. Closed Items

### 4.1 Recently Closed Risks
<prompt: What risks have been recently closed?>
{{for_each_closed_risk}}
- Risk ID: {{risk_id}}
  - Description: {{risk_description}}
  - Final Impact: {{final_impact}}
  - Resolution: {{resolution_details}}
  - Closure Date: {{closure_date}}
  - Lessons Learned: {{lessons_learned}}
{{end_for_each}}

### 4.2 Recently Closed Issues
<prompt: What issues have been recently closed?>
{{for_each_closed_issue}}
- Issue ID: {{issue_id}}
  - Description: {{issue_description}}
  - Final Impact: {{final_impact}}
  - Resolution: {{resolution_details}}
  - Closure Date: {{closure_date}}
  - Lessons Learned: {{lessons_learned}}
{{end_for_each}}

## 5. Classification Guidelines

### 5.1 Impact Levels
<prompt: How are impact levels defined?>
{{for_each_impact_level}}
- Level: {{impact_level}}
  - Definition: {{level_definition}}
  - Criteria: {{assessment_criteria}}
  - Examples: {{example_scenarios}}
{{end_for_each}}

### 5.2 Probability Levels
<prompt: How are probability levels defined?>
{{for_each_probability_level}}
- Level: {{probability_level}}
  - Definition: {{level_definition}}
  - Criteria: {{assessment_criteria}}
  - Examples: {{example_scenarios}}
{{end_for_each}}

### 5.3 Status Definitions
<prompt: What status types are used?>
{{for_each_status}}
- Status: {{status_name}}
  - Definition: {{status_definition}}
  - Usage Criteria: {{usage_criteria}}
  - Next Steps: {{typical_next_steps}}
{{end_for_each}}

## 6. Tracking Metrics

### 6.1 Risk Metrics
<prompt: What metrics are tracked for risks?>
{{for_each_risk_metric}}
- Metric: {{metric_name}}
  - Description: {{metric_description}}
  - Current Value: {{current_value}}
  - Target: {{target_value}}
  - Trend: {{trend_analysis}}
{{end_for_each}}

### 6.2 Issue Metrics
<prompt: What metrics are tracked for issues?>
{{for_each_issue_metric}}
- Metric: {{metric_name}}
  - Description: {{metric_description}}
  - Current Value: {{current_value}}
  - Target: {{target_value}}
  - Trend: {{trend_analysis}}
{{end_for_each}}

## Metadata
- Template Version: 1.0
- Last Updated: 2025-05-21
- Generated By: AI Documentation Assistant

## Appendices [Optional]
- Risk Categories: {{risk_categories}}
- Issue Categories: {{issue_categories}}
- Escalation Procedures: {{escalation_procedures}}
- Review Process: {{review_process}}
