# Technical Discovery and Recommendations Template

## Template Usage Instructions

This template guides AI systems in creating comprehensive technical discovery documents:
- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project needs

## 1. Executive Overview

### 1.1 Document Purpose
<prompt: What is the primary purpose of this technical discovery?>
- Primary Objective: {{primary_objective}}
- Target Audience: {{target_audience}}
- Expected Outcomes: {{expected_outcomes}}

### 1.2 Scope Definition
<prompt: What are the boundaries of this technical discovery?>
- In-Scope Areas:
{{for_each_scope_item}}
  - {{scope_item}}
    - Details: {{scope_details}}
    - Justification: {{scope_justification}}
{{end_for_each}}
- Out-of-Scope Areas:
{{for_each_exclusion}}
  - {{excluded_item}}
    - Rationale: {{exclusion_rationale}}
{{end_for_each}}

## 2. Current State Assessment

### 2.1 Infrastructure Analysis
<prompt: What is the current state of technical infrastructure?>
{{for_each_infrastructure_component}}
- Component: {{component_name}}
  - Current State: {{current_state}}
  - Limitations: {{limitations}}
  - Dependencies: {{dependencies}}
{{end_for_each}}

### 2.2 Process Analysis
<prompt: What are the current technical processes and workflows?>
{{for_each_process}}
- Process: {{process_name}}
  - Description: {{process_description}}
  - Tools Used: {{tools_used}}
  - Pain Points: {{pain_points}}
{{end_for_each}}

### 2.3 Security Assessment
<prompt: What is the current security posture?>
{{for_each_security_aspect}}
- Aspect: {{security_aspect}}
  - Current State: {{current_state}}
  - Vulnerabilities: {{vulnerabilities}}
  - Compliance Status: {{compliance_status}}
{{end_for_each}}

## 3. Gap Analysis

### 3.1 Technical Gaps
<prompt: What technical gaps exist between current and desired state?>
{{for_each_gap}}
- Gap Area: {{gap_area}}
  - Description: {{gap_description}}
  - Impact: {{gap_impact}}
  - Priority: {{gap_priority}}
{{end_for_each}}

### 3.2 Process Gaps
<prompt: What process-related gaps need to be addressed?>
{{for_each_process_gap}}
- Process Gap: {{process_gap}}
  - Current Process: {{current_process}}
  - Desired Process: {{desired_process}}
  - Impact: {{gap_impact}}
{{end_for_each}}

## 4. Future State Architecture

### 4.1 Technical Vision
<prompt: What is the proposed technical architecture?>
- Architecture Overview: {{architecture_overview}}
- Key Components:
{{for_each_component}}
  - Component: {{component_name}}
    - Purpose: {{component_purpose}}
    - Benefits: {{component_benefits}}
    - Integration Points: {{integration_points}}
{{end_for_each}}

### 4.2 Technology Stack
<prompt: What technologies are recommended?>
{{for_each_technology}}
- Category: {{technology_category}}
  - Recommended Solution: {{solution_name}}
  - Version: {{version}}
  - Justification: {{selection_rationale}}
{{end_for_each}}

## 5. Implementation Recommendations

### 5.1 Technical Recommendations
<prompt: What specific technical changes are recommended?>
{{for_each_recommendation}}
- Recommendation: {{recommendation_title}}
  - Description: {{recommendation_details}}
  - Priority: {{priority_level}}
  - Expected Benefits: {{expected_benefits}}
  - Implementation Complexity: {{complexity_level}}
{{end_for_each}}

### 5.2 Implementation Phases
<prompt: How should the implementation be phased?>
{{for_each_phase}}
- Phase: {{phase_name}}
  - Timeline: {{timeline}}
  - Key Activities: {{key_activities}}
  - Dependencies: {{dependencies}}
  - Success Criteria: {{success_criteria}}
{{end_for_each}}

## 6. Risk Assessment

### 6.1 Implementation Risks
<prompt: What risks should be considered?>
{{for_each_risk}}
- Risk: {{risk_description}}
  - Impact: {{risk_impact}}
  - Probability: {{risk_probability}}
  - Mitigation Strategy: {{mitigation_strategy}}
{{end_for_each}}

## 7. Resource Requirements

### 7.1 Team Resources
<prompt: What team resources are needed?>
{{for_each_role}}
- Role: {{role_name}}
  - Skills Required: {{required_skills}}
  - Responsibilities: {{responsibilities}}
  - Time Commitment: {{time_commitment}}
{{end_for_each}}

### 7.2 Infrastructure Resources
<prompt: What infrastructure resources are needed?>
{{for_each_resource}}
- Resource: {{resource_name}}
  - Specifications: {{specifications}}
  - Purpose: {{resource_purpose}}
  - Cost Estimate: {{cost_estimate}} [Optional]
{{end_for_each}}

## 8. Success Criteria

### 8.1 Technical Success Metrics
<prompt: How will technical success be measured?>
{{for_each_metric}}
- Metric: {{metric_name}}
  - Description: {{metric_description}}
  - Target Value: {{target_value}}
  - Measurement Method: {{measurement_method}}
{{end_for_each}}

## 9. Next Steps

### 9.1 Immediate Actions
<prompt: What immediate actions are recommended?>
{{for_each_action}}
- Action: {{action_description}}
  - Owner: {{action_owner}}
  - Timeline: {{action_timeline}}
  - Dependencies: {{action_dependencies}}
{{end_for_each}}

## Metadata
- Template Version: 1.0
- Last Updated: 2025-05-21
- Generated By: AI Documentation Assistant

## Appendices [Optional]
- Architecture Diagrams: {{architecture_diagrams}}
- Technical Specifications: {{technical_specs}}
- Reference Documents: {{reference_docs}}
- Glossary: {{glossary_terms}}
