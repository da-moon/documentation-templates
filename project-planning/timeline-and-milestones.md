# Project Timeline and Milestones Template

## Template Usage Instructions

This template helps AI systems generate comprehensive project timelines:
- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project needs

## 1. Project Overview

### 1.1 Basic Information
<prompt: What are the fundamental details of this project?>
- Project Name: {{project_name}}
- Project Duration: {{start_date}} to {{end_date}}
- Project Manager: {{project_manager}}
- Project Sponsor: {{project_sponsor}}

### 1.2 Project Context
<prompt: What is the strategic context of this project?>
- Business Objective: {{business_objective}}
- Strategic Alignment: {{strategic_alignment}}
- Expected Impact: {{expected_impact}}

## 2. Project Phases

### 2.1 Phase Overview
<prompt: What are the main phases of this project?>
{{for_each_phase}}
- Phase: {{phase_name}}
  - Timeline: {{start_date}} to {{end_date}}
  - Objectives: {{phase_objectives}}
  - Key Deliverables: {{key_deliverables}}
{{end_for_each}}

## 3. Detailed Timeline

### 3.1 Key Milestones
<prompt: What are the critical milestones in this project?>
{{for_each_milestone}}
- Milestone: {{milestone_name}}
  - Target Date: {{target_date}}
  - Description: {{milestone_description}}
  - Success Criteria: {{success_criteria}}
  - Dependencies: {{dependencies}}
{{end_for_each}}

### 3.2 Detailed Activities
<prompt: What specific activities are planned for each phase?>
{{for_each_phase}}
#### Phase: {{phase_name}}
{{for_each_activity}}
- Activity: {{activity_name}}
  - Duration: {{duration}}
  - Start Date: {{start_date}}
  - End Date: {{end_date}}
  - Owner: {{activity_owner}}
  - Dependencies: {{activity_dependencies}}
{{end_for_each}}
{{end_for_each}}

## 4. Critical Path Analysis

### 4.1 Critical Path Items
<prompt: What activities are on the critical path?>
{{for_each_critical_item}}
- Item: {{item_name}}
  - Impact: {{impact_description}}
  - Risk Level: {{risk_level}}
  - Mitigation Strategy: {{mitigation_strategy}}
{{end_for_each}}

### 4.2 Dependencies
<prompt: What are the key dependencies in the project?>
{{for_each_dependency}}
- Dependency: {{dependency_name}}
  - Type: {{dependency_type}}
  - Impact: {{dependency_impact}}
  - Owner: {{dependency_owner}}
  - Status: {{dependency_status}}
{{end_for_each}}

## 5. Resource Allocation

### 5.1 Team Resources
<prompt: What team resources are needed throughout the project?>
{{for_each_role}}
- Role: {{role_name}}
  - Phase Involvement: {{phase_involvement}}
  - Time Commitment: {{time_commitment}}
  - Key Responsibilities: {{responsibilities}}
{{end_for_each}}

### 5.2 Other Resources
<prompt: What additional resources are required?>
{{for_each_resource}}
- Resource: {{resource_name}}
  - Type: {{resource_type}}
  - Timeline: {{resource_timeline}}
  - Purpose: {{resource_purpose}}
{{end_for_each}}

## 6. Risk Management Timeline

### 6.1 Risk Monitoring Schedule
<prompt: How will risks be monitored throughout the project?>
{{for_each_risk_category}}
- Category: {{risk_category}}
  - Monitoring Frequency: {{monitoring_frequency}}
  - Review Points: {{review_points}}
  - Response Time: {{response_time}}
{{end_for_each}}

## 7. Progress Tracking

### 7.1 Reporting Schedule
<prompt: What is the reporting structure for this project?>
{{for_each_report_type}}
- Report: {{report_type}}
  - Frequency: {{frequency}}
  - Audience: {{audience}}
  - Key Metrics: {{key_metrics}}
{{end_for_each}}

### 7.2 KPIs and Metrics
<prompt: What metrics will be used to track progress?>
{{for_each_kpi}}
- KPI: {{kpi_name}}
  - Description: {{kpi_description}}
  - Target: {{target_value}}
  - Measurement Method: {{measurement_method}}
{{end_for_each}}

## 8. Change Management

### 8.1 Change Control Process
<prompt: How will timeline changes be managed?>
- Change Request Process: {{change_process}}
- Approval Requirements: {{approval_requirements}}
- Impact Assessment: {{impact_assessment}}

## Metadata
- Template Version: 1.0
- Last Updated: 2025-05-21
- Generated By: AI Documentation Assistant

## Appendices [Optional]
- Gantt Chart: {{gantt_chart}}
- Resource Calendar: {{resource_calendar}}
- Dependency Matrix: {{dependency_matrix}}
- Contact List: {{contact_list}}
