# Gap Analysis and Implementation Planning Template

## Template Usage Instructions

This template guides AI systems in creating comprehensive gap analysis and
implementation plans:

- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project complexity

## 1. Current State vs. Requirements Gap Assessment

### 1.1 Capability Gap Analysis Framework

<prompt: What are the key gaps between current capabilities and project
requirements?>

**Current State Assessment Summary**

- Existing Platform Capabilities: {{current_capabilities}}
- Current Data Assets and Sources: {{current_data_assets}}
- Team Skills and Resources: {{current_team_capabilities}}
- Infrastructure and Technology: {{current_infrastructure}}
- Processes and Governance: {{current_processes}}

**Target State Requirements Summary**

- Business Requirements and Objectives: {{target_business_requirements}}
- Technical Requirements and Specifications: {{target_technical_requirements}}
- User Experience and Functionality Needs: {{target_user_requirements}}
- Performance and Scalability Requirements: {{target_performance_requirements}}
- Compliance and Governance Requirements: {{target_governance_requirements}}

### 1.2 Detailed Gap Identification

<prompt: What specific gaps exist in each area that need to be addressed?>

{{for_each_gap_category}} **{{gap_category}} Gaps**

**Critical Gaps (Project Blockers)** {{for_each_critical_gap}}

- Gap Description: {{gap_description}}
- Current State: {{current_state}}
- Required State: {{required_state}}
- Business Impact: {{business_impact}}
- Technical Impact: {{technical_impact}}
- Dependencies: {{gap_dependencies}} {{end_for_each}}

**Significant Gaps (Major Impact)** {{for_each_significant_gap}}

- Gap Description: {{gap_description}}
- Current State: {{current_state}}
- Required State: {{required_state}}
- Impact Assessment: {{impact_assessment}}
- Resolution Complexity: {{resolution_complexity}} {{end_for_each}}

**Minor Gaps (Enhancement Opportunities)** {{for_each_minor_gap}}

- Gap Description: {{gap_description}}
- Improvement Opportunity: {{improvement_opportunity}}
- Value Potential: {{value_potential}}
- Resource Requirements: {{resource_requirements}} {{end_for_each}}
  {{end_for_each}}

## 2. Stakeholder Requirement Conflicts and Resolution

### 2.1 Requirement Conflict Analysis

<prompt: What conflicting requirements exist between different stakeholders or
constraints?>

**Identified Requirement Conflicts** {{for_each_conflict}} **Conflict:
{{conflict_name}}**

- Conflicting Requirements: {{conflicting_requirements}}
- Stakeholders Involved: {{conflicting_stakeholders}}
- Nature of Conflict: {{conflict_nature}}
- Business Impact of Conflict: {{conflict_impact}}
- Technical Constraints: {{technical_constraints}} {{end_for_each}}

**Resource and Priority Conflicts**

- Budget and Resource Limitations: {{resource_limitations}}
- Timeline and Scope Conflicts: {{timeline_conflicts}}
- Quality vs. Speed Trade-offs: {{quality_speed_tradeoffs}}
- Innovation vs. Stability Tensions: {{innovation_stability_tensions}}

### 2.2 Conflict Resolution Strategy

<prompt: How will requirement conflicts be resolved and stakeholder alignment
achieved?>

**Conflict Resolution Framework** {{for_each_conflict_resolution}}
**{{conflict_name}} Resolution**

- Resolution Approach: {{resolution_approach}}
- Compromise Strategy: {{compromise_strategy}}
- Stakeholder Agreement Process: {{agreement_process}}
- Decision-Making Authority: {{decision_authority}}
- Implementation Impact: {{implementation_impact}} {{end_for_each}}

**Stakeholder Alignment Process**

- Requirement Prioritization Method: {{prioritization_method}}
- Trade-off Decision Framework: {{tradeoff_framework}}
- Stakeholder Communication Plan: {{communication_plan}}
- Approval and Sign-off Process: {{approval_process}}

## 3. Technical Capability and Infrastructure Gaps

### 3.1 Technology and Platform Gaps

<prompt: What technology and infrastructure gaps need to be addressed?>

**Platform and Technology Assessment** {{for_each_technology_area}}
**{{technology_area}}**

- Current Capability: {{current_capability}}
- Required Capability: {{required_capability}}
- Gap Analysis: {{capability_gap}}
- Upgrade vs. Replace Decision: {{upgrade_replace_decision}}
- Migration Complexity: {{migration_complexity}}
- Cost Implications: {{cost_implications}} {{end_for_each}}

**Infrastructure and Architecture Gaps**

- Computing and Storage Capacity: {{capacity_gaps}}
- Network and Connectivity Requirements: {{connectivity_gaps}}
- Security and Compliance Infrastructure: {{security_gaps}}
- Integration and API Capabilities: {{integration_gaps}}
- Monitoring and Management Tools: {{monitoring_gaps}}

### 3.2 Data and Integration Gaps

<prompt: What data and integration capabilities are missing or insufficient?>

**Data Quality and Availability Gaps** {{for_each_data_gap}}
**{{data_category}}**

- Current Data State: {{current_data_state}}
- Required Data Quality: {{required_data_quality}}
- Data Availability Gaps: {{availability_gaps}}
- Integration Complexity: {{integration_complexity}}
- Quality Improvement Requirements: {{quality_requirements}} {{end_for_each}}

**Integration and API Gaps**

- Source System Integration: {{source_integration_gaps}}
- Real-time vs. Batch Processing: {{processing_gaps}}
- Data Transformation Capabilities: {{transformation_gaps}}
- Error Handling and Monitoring: {{error_handling_gaps}}

## 4. Skills and Resource Gap Assessment

### 4.1 Team Capability Analysis

<prompt: What skills and resource gaps exist in the current team?>

**Technical Skills Gap Assessment** {{for_each_skill_area}} **{{skill_area}}**

- Current Team Proficiency: {{current_proficiency}}
- Required Skill Level: {{required_skill_level}}
- Skill Gap Severity: {{gap_severity}}
- Training vs. Hiring Decision: {{training_hiring_decision}}
- Development Timeline: {{skill_development_timeline}} {{end_for_each}}

**Resource Capacity and Availability**

- Current Team Capacity: {{current_capacity}}
- Project Resource Requirements: {{resource_requirements}}
- Capacity Gap Analysis: {{capacity_gaps}}
- External Resource Needs: {{external_resource_needs}}
- Resource Allocation Conflicts: {{allocation_conflicts}}

### 4.2 Organizational and Process Gaps

<prompt: What organizational and process changes are needed to support the
project?>

**Process and Methodology Gaps**

- Current Process Maturity: {{current_process_maturity}}
- Required Process Capabilities: {{required_processes}}
- Governance and Oversight Gaps: {{governance_gaps}}
- Change Management Needs: {{change_management_needs}}

**Organizational Structure and Culture**

- Organizational Alignment: {{organizational_alignment}}
- Culture and Change Readiness: {{culture_readiness}}
- Communication and Collaboration: {{collaboration_gaps}}
- Decision-Making and Authority: {{decision_making_gaps}}

## 5. Implementation Strategy and Sequencing

### 5.1 Priority-Based Implementation Planning

<prompt: What is the optimal sequence for addressing identified gaps?>

**Gap Prioritization Framework**

- Business Impact Scoring: {{business_impact_scoring}}
- Technical Complexity Assessment: {{complexity_assessment}}
- Resource Requirement Analysis: {{resource_analysis}}
- Risk Level Evaluation: {{risk_evaluation}}
- Dependency Mapping: {{dependency_mapping}}

**Implementation Phase Design** {{for_each_phase}} **Phase {{phase_number}}:
{{phase_name}} ({{phase_duration}})**

- Primary Objectives: {{phase_objectives}}
- Gap Resolution Targets: {{gap_targets}}
- Key Deliverables: {{phase_deliverables}}
- Success Criteria: {{success_criteria}}
- Resource Allocation: {{resource_allocation}}
- Risk Factors: {{phase_risks}} {{end_for_each}}

### 5.2 Quick Wins and Foundation Building

<prompt: What quick wins can be achieved while building long-term
capabilities?>

**Quick Win Identification and Planning** {{for_each_quick_win}}
**{{quick_win_name}}**

- Description and Value: {{quick_win_description}}
- Implementation Effort: {{implementation_effort}}
- Expected Timeline: {{quick_win_timeline}}
- Success Metrics: {{quick_win_metrics}}
- Foundation Building Contribution: {{foundation_contribution}}
  {{end_for_each}}

**Foundation Building Strategy**

- Core Infrastructure Development: {{infrastructure_foundation}}
- Team Capability Building: {{capability_foundation}}
- Process and Governance Establishment: {{process_foundation}}
- Technology Platform Preparation: {{platform_foundation}}

## 6. Resource Planning and Budget Allocation

### 6.1 Resource Requirement Analysis

<prompt: What resources are needed to address identified gaps?>

**Human Resource Requirements** {{for_each_resource_category}}
**{{resource_category}}**

- Full-Time Resource Needs: {{fulltime_needs}}
- Part-Time and Consulting Needs: {{parttime_consulting_needs}}
- Skill Level Requirements: {{skill_requirements}}
- Duration and Timeline: {{resource_timeline}}
- Internal vs. External Sourcing: {{sourcing_strategy}} {{end_for_each}}

**Technology and Infrastructure Investment**

- Software Licensing and Subscriptions: {{software_costs}}
- Hardware and Infrastructure Costs: {{infrastructure_costs}}
- Training and Certification Expenses: {{training_costs}}
- External Services and Consulting: {{external_service_costs}}

### 6.2 Budget Planning and Cost Management

<prompt: How should budget be allocated and managed across implementation
phases?>

**Budget Allocation Strategy** {{for_each_budget_category}}
**{{budget_category}}**

- Phase 1 Allocation: {{phase1_budget}}
- Phase 2 Allocation: {{phase2_budget}}
- Phase 3+ Allocation: {{future_phase_budget}}
- Contingency Planning: {{contingency_budget}}
- ROI and Value Justification: {{roi_justification}} {{end_for_each}}

**Cost Management and Control**

- Budget Monitoring and Reporting: {{budget_monitoring}}
- Cost Control Mechanisms: {{cost_controls}}
- Value Realization Tracking: {{value_tracking}}
- Budget Adjustment Procedures: {{budget_adjustments}}

## 7. Risk Management and Mitigation Planning

### 7.1 Implementation Risk Assessment

<prompt: What risks could impact successful gap resolution and implementation?>

**Risk Categories and Assessment** {{for_each_risk_category}}
**{{risk_category}} Risks**

- High Impact Risks: {{high_impact_risks}}
- Medium Impact Risks: {{medium_impact_risks}}
- Low Impact Risks: {{low_impact_risks}}
- Cross-Cutting Risks: {{cross_cutting_risks}} {{end_for_each}}

**Risk Impact and Probability Analysis** {{for_each_major_risk}}
**{{risk_name}}**

- Risk Description: {{risk_description}}
- Probability Assessment: {{probability_assessment}}
- Impact Assessment: {{impact_assessment}}
- Risk Score: {{risk_score}}
- Early Warning Indicators: {{warning_indicators}} {{end_for_each}}

### 7.2 Risk Mitigation and Contingency Planning

<prompt: How will identified risks be mitigated and managed?>

**Risk Mitigation Strategies** {{for_each_mitigation_strategy}} **{{risk_name}}
Mitigation**

- Primary Mitigation Approach: {{primary_mitigation}}
- Secondary Mitigation Options: {{secondary_mitigation}}
- Contingency Plans: {{contingency_plans}}
- Resource Requirements: {{mitigation_resources}}
- Success Indicators: {{mitigation_success_indicators}} {{end_for_each}}

**Risk Monitoring and Response**

- Risk Monitoring Framework: {{risk_monitoring}}
- Escalation Procedures: {{escalation_procedures}}
- Response Team and Responsibilities: {{response_team}}
- Communication and Reporting: {{risk_communication}}

## 8. Success Measurement and Progress Tracking

### 8.1 Success Criteria and KPIs

<prompt: How will successful gap resolution and implementation be measured?>

**Gap Resolution Success Metrics** {{for_each_gap_category}} **{{gap_category}}
Success Metrics**

- Gap Closure Indicators: {{closure_indicators}}
- Performance Improvement Metrics: {{performance_metrics}}
- Quality and Effectiveness Measures: {{quality_measures}}
- User Satisfaction and Adoption: {{satisfaction_measures}} {{end_for_each}}

**Overall Project Success KPIs**

- Business Value Realization: {{business_value_kpis}}
- Technical Performance Achievement: {{technical_performance_kpis}}
- User Adoption and Satisfaction: {{adoption_kpis}}
- Process and Efficiency Improvements: {{efficiency_kpis}}

### 8.2 Progress Monitoring and Reporting

<prompt: How will progress be monitored and communicated to stakeholders?>

**Progress Tracking Framework**

- Milestone Tracking and Reporting: {{milestone_tracking}}
- KPI Monitoring and Analysis: {{kpi_monitoring}}
- Risk and Issue Tracking: {{risk_issue_tracking}}
- Budget and Resource Utilization: {{resource_tracking}}

**Stakeholder Communication and Reporting** {{for_each_stakeholder_group}}
**{{stakeholder_group}}**

- Reporting Frequency: {{reporting_frequency}}
- Report Content and Format: {{report_format}}
- Communication Channels: {{communication_channels}}
- Escalation and Decision Points: {{escalation_points}} {{end_for_each}}

## 9. Change Management and Stakeholder Engagement

### 9.1 Change Management Strategy

<prompt: How will organizational change be managed throughout implementation?>

**Change Management Framework**

- Change Impact Assessment: {{change_impact}}
- Stakeholder Change Readiness: {{change_readiness}}
- Resistance Management Strategy: {{resistance_management}}
- Communication and Engagement Plan: {{engagement_plan}}

**Training and Support Strategy** {{for_each_user_group}} **{{user_group}}**

- Training Requirements: {{training_requirements}}
- Support and Assistance Needs: {{support_needs}}
- Change Champion Program: {{champion_program}}
- Feedback and Improvement Process: {{feedback_process}} {{end_for_each}}

### 9.2 Continuous Improvement and Evolution

<prompt: How will the implementation plan evolve based on learning and changing
requirements?>

**Continuous Improvement Framework**

- Regular Plan Review and Update Cycles: {{review_cycles}}
- Lessons Learned Capture and Application: {{lessons_learned}}
- Best Practice Identification and Sharing: {{best_practices}}
- Plan Adaptation and Optimization: {{plan_optimization}}

**Long-term Sustainability and Growth**

- Capability Maintenance and Support: {{capability_maintenance}}
- Knowledge Transfer and Documentation: {{knowledge_transfer}}
- Scaling Strategy and Approach: {{scaling_strategy}}
- Strategic Alignment and Value Optimization: {{strategic_alignment}}

## Metadata

- Template Version: 1.0
- Last Updated: 2025-05-21
- Use Case: Data and Analytics Project Gap Analysis and Implementation Planning
- Applicable Scenarios: Data Warehousing, BI Implementation, Analytics Platform
  Development, Digital Transformation
