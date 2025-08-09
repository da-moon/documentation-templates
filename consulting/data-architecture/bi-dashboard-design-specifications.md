# Business Intelligence Dashboard Design Template

## Template Usage Instructions

This template guides AI systems in creating effective BI dashboard design
specifications:

- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on platform and complexity

## 1. Dashboard Strategy and Audience Analysis

### 1.1 Stakeholder and User Analysis

<prompt: Who are the primary users of these dashboards and what are their
specific needs?>

**Primary Stakeholder Groups** {{for_each_stakeholder_group}}
**{{stakeholder_group}}**

- Role and Responsibilities: {{stakeholder_responsibilities}}
- Decision-Making Authority: {{decision_authority}}
- Information Needs: {{information_needs}}
- Technical Proficiency: {{technical_proficiency}}
- Access Frequency: {{access_frequency}}
- Preferred Interaction Style: {{interaction_style}}
- Success Criteria: {{stakeholder_success_criteria}} {{end_for_each}}

**User Journey and Workflow Analysis**

- Primary Use Cases: {{primary_use_cases}}
- Typical User Sessions: {{typical_sessions}}
- Decision-Making Workflows: {{decision_workflows}}
- Information Discovery Patterns: {{discovery_patterns}}
- Collaboration and Sharing Needs: {{collaboration_needs}}

### 1.2 Business Context and Objectives

<prompt: What business objectives do these dashboards need to support?>

**Business Objectives and KPIs**

- Primary Business Objectives: {{business_objectives}}
- Key Performance Indicators: {{key_performance_indicators}}
- Success Measurement Criteria: {{success_measurement}}
- Decision Support Requirements: {{decision_support_needs}}
- Competitive and Market Context: {{market_context}}

**Information Architecture Requirements**

- Data Granularity Needs: {{data_granularity}}
- Time Horizon Requirements: {{time_horizons}}
- Benchmark and Comparison Needs: {{benchmark_requirements}}
- Drill-Down and Investigation Requirements: {{drilldown_needs}}

## 2. Dashboard Architecture and Navigation Design

### 2.1 Dashboard Hierarchy and Organization

<prompt: How should dashboards be organized and connected to support user
workflows?>

**Dashboard Structure Strategy**

- Overall Architecture Pattern: {{architecture_pattern}} (Pyramid,
  Hub-and-spoke, Workflow-based)
- Navigation Hierarchy: {{navigation_hierarchy}}
- Dashboard Categorization: {{dashboard_categories}}
- Cross-Dashboard Linking Strategy: {{linking_strategy}}

**Dashboard Types and Purposes** {{for_each_dashboard_type}}
**{{dashboard_type}}**

- Primary Purpose: {{dashboard_purpose}}
- Target Audience: {{target_audience}}
- Key Metrics and Content: {{key_content}}
- Update Frequency: {{update_frequency}}
- Interaction Complexity: {{interaction_complexity}}
- Performance Requirements: {{performance_requirements}} {{end_for_each}}

### 2.2 Information Flow and User Experience Design

<prompt: How should users navigate through information to support their
decision-making?>

**User Experience Flow Design**

- Entry Points and Landing Strategy: {{entry_points}}
- Progressive Disclosure Strategy: {{progressive_disclosure}}
- Context Preservation Approach: {{context_preservation}}
- Search and Discovery Features: {{search_features}}

**Navigation and Interaction Patterns**

- Primary Navigation Methods: {{navigation_methods}}
- Filtering and Segmentation Strategy: {{filtering_strategy}}
- Drill-Down and Detail Investigation: {{drilldown_strategy}}
- Cross-Dashboard Navigation: {{cross_navigation}}

## 3. Visual Design and Data Presentation

### 3.1 Visual Design Framework

<prompt: What visual design principles and standards should guide dashboard
creation?>

**Design System and Standards**

- Color Palette and Coding Strategy: {{color_strategy}}
- Typography and Text Hierarchy: {{typography_standards}}
- Layout and Grid System: {{layout_standards}}
- Iconography and Visual Elements: {{iconography_standards}}
- Branding and Identity Integration: {{branding_requirements}}

**Visualization Selection Criteria** {{for_each_visualization_type}}
**{{visualization_type}}**

- Optimal Use Cases: {{optimal_use_cases}}
- Data Type Requirements: {{data_requirements}}
- Audience Considerations: {{audience_considerations}}
- Platform Implementation Notes: {{platform_notes}}
- Performance Implications: {{performance_implications}} {{end_for_each}}

### 3.2 Data Presentation and Storytelling

<prompt: How should data be presented to support understanding and
decision-making?>

**Data Storytelling Framework**

- Narrative Structure: {{narrative_structure}}
- Key Message Hierarchy: {{message_hierarchy}}
- Supporting Detail Organization: {{detail_organization}}
- Context and Comparison Strategy: {{context_strategy}}

**Metric Definition and Presentation** {{for_each_metric_category}}
**{{metric_category}}**

- Key Metrics: {{key_metrics}}
- Calculation Methodology: {{calculation_methodology}}
- Presentation Format: {{presentation_format}}
- Benchmark and Target Integration: {{benchmark_integration}}
- Trend and Historical Context: {{historical_context}} {{end_for_each}}

## 4. Technical Implementation Specifications

### 4.1 Platform-Specific Design Requirements

<prompt: What are the technical requirements and constraints for your BI
platform?>

**BI Platform Configuration**

- Primary BI Platform: {{bi_platform}} (Tableau, Power BI, Grafana, Looker,
  etc.)
- Version and Edition: {{platform_version}}
- Licensing and User Constraints: {{licensing_constraints}}
- Performance Characteristics: {{platform_performance}}
- Integration Capabilities: {{integration_capabilities}}

**Data Source Integration Design** {{for_each_data_source}}
**{{data_source_name}}**

- Connection Method: {{connection_method}}
- Data Refresh Strategy: {{refresh_strategy}}
- Performance Optimization: {{performance_optimization}}
- Security and Access Control: {{security_requirements}}
- Error Handling and Monitoring: {{error_handling}} {{end_for_each}}

### 4.2 Performance and Scalability Design

<prompt: What performance requirements must the dashboards meet?>

**Performance Requirements by Dashboard Type** {{for_each_performance_tier}}
**{{performance_tier}}**

- Load Time Targets: {{load_time_targets}}
- Query Response Time Limits: {{query_response_limits}}
- Concurrent User Capacity: {{concurrent_capacity}}
- Data Refresh Frequency: {{refresh_frequency}}
- Caching Strategy: {{caching_strategy}} {{end_for_each}}

**Scalability and Optimization Strategy**

- Query Optimization Approach: {{query_optimization}}
- Data Model Optimization: {{data_model_optimization}}
- Caching and Performance Enhancement: {{performance_enhancement}}
- Resource Management and Allocation: {{resource_management}}

## 5. Interactivity and User Engagement Features

### 5.1 Interactive Features and Controls

<prompt: What interactive features should be included to enhance user
engagement and analysis?>

**Filtering and Parameter Controls** {{for_each_filter_type}}
**{{filter_type}}**

- Purpose and Use Cases: {{filter_purpose}}
- Implementation Method: {{filter_implementation}}
- Default Values and Behavior: {{default_behavior}}
- Cross-Dashboard Impact: {{cross_dashboard_impact}}
- Performance Considerations: {{filter_performance}} {{end_for_each}}

**Drill-Down and Investigation Features**

- Drill-Down Hierarchy Design: {{drilldown_hierarchy}}
- Context Menu and Action Options: {{context_actions}}
- Detail View and Modal Design: {{detail_views}}
- Export and Sharing Capabilities: {{export_capabilities}}

### 5.2 Personalization and Customization

<prompt: What personalization and customization options should be available?>

**User Customization Features**

- Dashboard Layout Customization: {{layout_customization}}
- Metric and View Preferences: {{metric_preferences}}
- Alert and Notification Settings: {{notification_settings}}
- Personal Dashboard Creation: {{personal_dashboards}}

**Role-Based Configuration** {{for_each_user_role}} **{{user_role}}**

- Default Dashboard Configuration: {{default_configuration}}
- Available Customization Options: {{customization_options}}
- Data Access Permissions: {{data_permissions}}
- Feature Access Controls: {{feature_controls}} {{end_for_each}}

## 6. Security and Access Control Design

### 6.1 Data Security and Privacy

<prompt: What security and privacy requirements affect dashboard design?>

**Data Access and Security Controls**

- Role-Based Access Control (RBAC): {{rbac_implementation}}
- Row-Level and Column-Level Security: {{granular_security}}
- Data Masking and Anonymization: {{data_masking}}
- Audit Logging and Compliance: {{audit_requirements}}

**Privacy and Compliance Requirements** {{for_each_compliance_requirement}}

- Regulation: {{regulation_name}}
- Data Protection Requirements: {{data_protection}}
- Access Control Requirements: {{access_control}}
- Documentation and Reporting: {{compliance_reporting}} {{end_for_each}}

### 6.2 User Authentication and Authorization

<prompt: How should user authentication and authorization be implemented?>

**Authentication Strategy**

- Single Sign-On (SSO) Integration: {{sso_integration}}
- Multi-Factor Authentication (MFA): {{mfa_requirements}}
- Session Management: {{session_management}}
- Password and Security Policies: {{security_policies}}

**Authorization and Permission Management**

- Permission Inheritance and Hierarchy: {{permission_hierarchy}}
- Dynamic Permission Assignment: {{dynamic_permissions}}
- Guest and External User Access: {{external_access}}
- Permission Audit and Review: {{permission_audit}}

## 7. Training and User Adoption Strategy

### 7.1 User Training and Documentation

<prompt: What training and documentation is needed to support user adoption?>

**Training Program Design** {{for_each_user_group}} **{{user_group}}**

- Training Objectives: {{training_objectives}}
- Training Methods and Materials: {{training_methods}}
- Skill Development Path: {{skill_development}}
- Assessment and Certification: {{assessment_methods}} {{end_for_each}}

**Documentation and Support Materials**

- User Guides and Quick Reference: {{user_guides}}
- Video Tutorials and Walkthroughs: {{video_tutorials}}
- FAQ and Troubleshooting: {{faq_support}}
- Advanced Features and Tips: {{advanced_guides}}

### 7.2 Change Management and Adoption Support

<prompt: How will dashboard adoption and change management be supported?>

**Adoption Strategy and Support**

- Rollout and Deployment Strategy: {{rollout_strategy}}
- Champion and Super User Program: {{champion_program}}
- Feedback Collection and Integration: {{feedback_processes}}
- Continuous Improvement Process: {{improvement_process}}

**Success Measurement and Optimization**

- User Adoption Metrics: {{adoption_metrics}}
- Usage Analytics and Insights: {{usage_analytics}}
- User Satisfaction Measurement: {{satisfaction_measurement}}
- Dashboard Effectiveness Assessment: {{effectiveness_assessment}}

## 8. Maintenance and Evolution Planning

### 8.1 Dashboard Lifecycle Management

<prompt: How will dashboards be maintained and evolved over time?>

**Maintenance and Update Procedures**

- Regular Review and Update Cycles: {{review_cycles}}
- Performance Monitoring and Optimization: {{performance_monitoring}}
- Data Quality and Accuracy Validation: {{quality_validation}}
- User Feedback Integration: {{feedback_integration}}

**Version Control and Change Management**

- Dashboard Version Control: {{version_control}}
- Change Approval and Testing: {{change_management}}
- Rollback and Recovery Procedures: {{rollback_procedures}}
- Documentation and Communication: {{change_communication}}

### 8.2 Platform Evolution and Technology Updates

<prompt: How will the dashboard platform evolve with technology changes?>

**Technology Evolution Planning**

- Platform Upgrade and Migration Planning: {{upgrade_planning}}
- New Feature Evaluation and Integration: {{feature_evaluation}}
- Legacy Dashboard Migration: {{legacy_migration}}
- Technology Roadmap Alignment: {{roadmap_alignment}}

**Continuous Improvement Framework**

- Performance Optimization Cycles: {{optimization_cycles}}
- User Experience Enhancement: {{ux_enhancement}}
- Feature Development Prioritization: {{feature_prioritization}}
- Innovation and Experimentation: {{innovation_processes}}

## Metadata

- Template Version: 1.0
- Last Updated: 2025-05-21
- Use Case: Business Intelligence Dashboard Design and Implementation
- Applicable Platforms: Tableau, Power BI, Grafana, Looker, QlikView, Sisense,
  and other BI platforms
