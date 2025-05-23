# Methodology and Approach Template

## Template Usage Instructions

This template helps AI systems create comprehensive methodology and approach documents:
- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project needs

## 1. Project Foundation

### 1.1 Basic Information
<prompt: What are the fundamental details of this project?>
- Project Name: {{project_name}}
- Project Category: {{project_category}}
- Document Owner: {{document_owner}}
- Last Updated: {{last_updated}}

### 1.2 Context and Purpose
<prompt: What is the strategic context and purpose of this project?>
- Business Context: {{business_context}}
- Project Purpose: {{project_purpose}}
- Strategic Alignment: {{strategic_alignment}}

## 2. Methodology Overview

### 2.1 Chosen Methodology
<prompt: What methodology will be used for this project?>
- Primary Methodology: {{methodology_name}}
- Key Principles: {{methodology_principles}}
- Rationale: {{methodology_rationale}}

### 2.2 Methodology Customization
<prompt: How will the methodology be adapted for this project?>
{{for_each_customization}}
- Aspect: {{customization_aspect}}
  - Standard Approach: {{standard_approach}}
  - Customization: {{customization_details}}
  - Justification: {{customization_rationale}}
{{end_for_each}}

## 3. Project Governance

### 3.1 Team Structure
<prompt: What is the project team structure?>
{{for_each_role}}
- Role: {{role_name}}
  - Responsibilities: {{responsibilities}}
  - Authority Level: {{authority_level}}
  - Reports To: {{reporting_line}}
{{end_for_each}}

### 3.2 Decision Making Framework
<prompt: How will decisions be made in the project?>
{{for_each_decision_type}}
- Type: {{decision_type}}
  - Authority Level: {{authority_level}}
  - Process: {{decision_process}}
  - Escalation Path: {{escalation_path}}
{{end_for_each}}

## 4. Project Phases

### 4.1 Phase Overview
<prompt: What are the main phases of this project?>
{{for_each_phase}}
- Phase: {{phase_name}}
  - Objectives: {{phase_objectives}}
  - Key Activities: {{key_activities}}
  - Deliverables: {{deliverables}}
  - Duration: {{duration}}
{{end_for_each}}

## 5. Quality Management

### 5.1 Quality Standards
<prompt: What quality standards will be applied?>
{{for_each_standard}}
- Standard: {{standard_name}}
  - Description: {{standard_description}}
  - Metrics: {{quality_metrics}}
  - Verification Method: {{verification_method}}
{{end_for_each}}

### 5.2 Review Process
<prompt: How will deliverables be reviewed and approved?>
{{for_each_review_type}}
- Type: {{review_type}}
  - Participants: {{participants}}
  - Frequency: {{frequency}}
  - Criteria: {{review_criteria}}
{{end_for_each}}

## 6. Risk Management

### 6.1 Risk Assessment
<prompt: How will risks be managed throughout the project?>
{{for_each_risk_category}}
- Category: {{risk_category}}
  - Assessment Method: {{assessment_method}}
  - Mitigation Strategy: {{mitigation_strategy}}
  - Monitoring Approach: {{monitoring_approach}}
{{end_for_each}}

## 7. Communication Strategy

### 7.1 Communication Channels
<prompt: What communication channels will be used?>
{{for_each_channel}}
- Channel: {{channel_name}}
  - Purpose: {{channel_purpose}}
  - Frequency: {{communication_frequency}}
  - Participants: {{participants}}
{{end_for_each}}

### 7.2 Reporting Structure
<prompt: What reports will be generated and distributed?>
{{for_each_report}}
- Report: {{report_name}}
  - Content: {{report_content}}
  - Frequency: {{report_frequency}}
  - Distribution: {{distribution_list}}
{{end_for_each}}

## 8. Change Management

### 8.1 Change Control Process
<prompt: How will changes be managed?>
- Process Overview: {{change_process}}
- Assessment Criteria: {{assessment_criteria}}
- Approval Workflow: {{approval_workflow}}

## 9. Success Criteria

### 9.1 Project Success Metrics
<prompt: How will project success be measured?>
{{for_each_metric}}
- Metric: {{metric_name}}
  - Description: {{metric_description}}
  - Target: {{target_value}}
  - Measurement Method: {{measurement_method}}
{{end_for_each}}

## Metadata
- Template Version: 1.0
- Last Updated: 2025-05-21
- Generated By: AI Documentation Assistant

## Appendices [Optional]
- Methodology Reference: {{methodology_reference}}
- Templates and Tools: {{templates_tools}}
- Glossary: {{glossary_terms}}
