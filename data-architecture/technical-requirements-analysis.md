# Technical Requirements Analysis Template

## Template Usage Instructions

This template helps AI systems translate business requirements into technical
specifications:

- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project complexity

## 1. Business Requirements Translation Framework

### 1.1 Business to Technical Requirement Mapping

<prompt: How do business requirements translate into specific technical
capabilities?>

**Business Requirement Analysis** {{for_each_business_requirement}}
**{{business_requirement_name}}**

- Business Objective: {{business_objective}}
- Stakeholder Impact: {{stakeholder_impact}}
- Success Criteria: {{success_criteria}}
- Technical Implications: {{technical_implications}}
- Performance Expectations: {{performance_expectations}}
- Compliance Requirements: {{compliance_requirements}} {{end_for_each}}

**Technical Capability Mapping** {{for_each_technical_capability}}
**{{technical_capability}}**

- Supporting Business Requirements: {{supporting_requirements}}
- Technical Specifications: {{technical_specifications}}
- Implementation Complexity: {{implementation_complexity}}
- Resource Requirements: {{resource_requirements}}
- Risk Factors: {{risk_factors}} {{end_for_each}}

### 1.2 User Experience and Functional Requirements

<prompt: What specific functional and user experience requirements must be
met?>

**User Experience Requirements** {{for_each_user_group}} **{{user_group}}**

- User Interface Requirements: {{ui_requirements}}
- Interaction Patterns: {{interaction_patterns}}
- Accessibility Requirements: {{accessibility_requirements}}
- Mobile and Device Support: {{device_support}}
- Performance Expectations: {{user_performance_expectations}} {{end_for_each}}

**Functional Requirements Specification** {{for_each_functional_area}}
**{{functional_area}}**

- Core Functions: {{core_functions}}
- Advanced Features: {{advanced_features}}
- Integration Requirements: {{integration_requirements}}
- Customization Needs: {{customization_needs}}
- Workflow Support: {{workflow_support}} {{end_for_each}}

## 2. System Architecture and Infrastructure Requirements

### 2.1 Architecture Patterns and Design Requirements

<prompt: What architectural patterns and design principles should guide the
technical implementation?>

**Architecture Framework Requirements**

- Overall Architecture Pattern: {{architecture_pattern}}
- Design Principles: {{design_principles}}
- Technology Stack Preferences: {{technology_stack}}
- Integration Architecture: {{integration_architecture}}
- Deployment Architecture: {{deployment_architecture}}

**Component Architecture Specifications** {{for_each_component}}
**{{component_name}}**

- Component Purpose: {{component_purpose}}
- Technical Requirements: {{component_requirements}}
- Interface Specifications: {{interface_specifications}}
- Performance Requirements: {{component_performance}}
- Scalability Needs: {{component_scalability}}
- Security Requirements: {{component_security}} {{end_for_each}}

### 2.2 Infrastructure and Platform Requirements

<prompt: What infrastructure capabilities and platform features are required?>

**Computing and Storage Requirements**

- Processing Power Requirements: {{processing_requirements}}
- Memory and Storage Specifications: {{storage_requirements}}
- Network and Bandwidth Needs: {{network_requirements}}
- Backup and Recovery Requirements: {{backup_requirements}}
- Disaster Recovery Specifications: {{disaster_recovery_requirements}}

**Platform and Environment Requirements** {{for_each_environment}}
**{{environment_name}}**

- Platform Requirements: {{platform_requirements}}
- Operating System Specifications: {{os_requirements}}
- Container and Orchestration Needs: {{container_requirements}}
- Cloud vs On-Premise Considerations: {{deployment_preferences}}
- Environment Configuration: {{environment_configuration}} {{end_for_each}}

## 3. Data Management and Integration Requirements

### 3.1 Data Architecture and Storage Requirements

<prompt: What data architecture and storage capabilities are needed?>

**Data Storage and Management Requirements**

- Data Volume and Growth Projections: {{data_volume_projections}}
- Data Type and Structure Requirements: {{data_structure_requirements}}
- Storage Performance Requirements: {{storage_performance}}
- Data Retention and Archival Needs: {{retention_requirements}}
- Backup and Recovery Specifications: {{data_backup_requirements}}

**Data Model and Schema Requirements** {{for_each_data_domain}}
**{{data_domain}}**

- Data Model Requirements: {{data_model_requirements}}
- Schema Design Specifications: {{schema_specifications}}
- Relationship and Constraint Definitions: {{relationship_requirements}}
- Indexing and Optimization Needs: {{indexing_requirements}}
- Version Control and Change Management: {{schema_change_management}}
  {{end_for_each}}

### 3.2 Data Integration and Processing Requirements

<prompt: What data integration and processing capabilities are required?>

**Data Integration Requirements** {{for_each_data_source}}
**{{data_source_name}}**

- Integration Method: {{integration_method}}
- Data Format and Protocol: {{data_format}}
- Frequency and Volume: {{integration_frequency}}
- Transformation Requirements: {{transformation_requirements}}
- Quality and Validation Needs: {{quality_requirements}}
- Error Handling Requirements: {{error_handling}} {{end_for_each}}

**Data Processing and Analytics Requirements**

- Real-Time Processing Needs: {{realtime_processing}}
- Batch Processing Requirements: {{batch_processing}}
- Analytics and Computation Needs: {{analytics_requirements}}
- Machine Learning and AI Integration: {{ml_requirements}}
- Complex Event Processing: {{event_processing}}

## 4. Performance and Scalability Requirements

### 4.1 Performance Specifications and Targets

<prompt: What specific performance requirements must the system meet?>

**System Performance Requirements** {{for_each_performance_category}}
**{{performance_category}}**

- Response Time Targets: {{response_time_targets}}
- Throughput Requirements: {{throughput_requirements}}
- Concurrency Support: {{concurrency_requirements}}
- Peak Load Handling: {{peak_load_requirements}}
- Performance Monitoring: {{performance_monitoring}} {{end_for_each}}

**User Experience Performance Requirements**

- Page Load Time Targets: {{page_load_targets}}
- Query Response Time Limits: {{query_response_limits}}
- Report Generation Performance: {{report_generation_performance}}
- Dashboard Refresh Performance: {{dashboard_refresh_performance}}
- Mobile Performance Specifications: {{mobile_performance}}

### 4.2 Scalability and Capacity Planning

<prompt: How should the system scale to meet growing demands?>

**Scalability Requirements**

- Horizontal Scaling Capabilities: {{horizontal_scaling}}
- Vertical Scaling Options: {{vertical_scaling}}
- Auto-Scaling Requirements: {{auto_scaling}}
- Geographic Distribution Needs: {{geographic_scaling}}
- Multi-Tenancy Requirements: {{multi_tenancy}}

**Capacity Planning Specifications** {{for_each_capacity_dimension}}
**{{capacity_dimension}}**

- Current Capacity Needs: {{current_capacity}}
- Growth Projections: {{growth_projections}}
- Peak Capacity Requirements: {{peak_capacity}}
- Scaling Triggers: {{scaling_triggers}}
- Resource Allocation Strategy: {{resource_allocation}} {{end_for_each}}

## 5. Security and Compliance Requirements

### 5.1 Security Architecture and Controls

<prompt: What security requirements and controls must be implemented?>

**Authentication and Authorization Requirements**

- Identity Management Integration: {{identity_management}}
- Authentication Methods: {{authentication_methods}}
- Single Sign-On (SSO) Requirements: {{sso_requirements}}
- Multi-Factor Authentication (MFA): {{mfa_requirements}}
- Role-Based Access Control (RBAC): {{rbac_requirements}}

**Data Security Requirements** {{for_each_security_control}}
**{{security_control}}**

- Security Control Description: {{control_description}}
- Implementation Requirements: {{implementation_requirements}}
- Compliance Standards: {{compliance_standards}}
- Monitoring and Auditing: {{monitoring_requirements}}
- Incident Response: {{incident_response}} {{end_for_each}}

### 5.2 Compliance and Regulatory Requirements

<prompt: What compliance and regulatory requirements affect the technical
implementation?>

**Regulatory Compliance Requirements** {{for_each_regulation}}
**{{regulation_name}}**

- Applicable Requirements: {{applicable_requirements}}
- Technical Controls Needed: {{technical_controls}}
- Data Protection Measures: {{data_protection}}
- Audit and Reporting Requirements: {{audit_requirements}}
- Documentation Needs: {{documentation_requirements}} {{end_for_each}}

**Privacy and Data Protection Requirements**

- Data Classification Requirements: {{data_classification}}
- Privacy Controls and Measures: {{privacy_controls}}
- Data Masking and Anonymization: {{data_masking}}
- Consent Management: {{consent_management}}
- Right to Deletion (Right to be Forgotten): {{deletion_rights}}

## 6. Integration and Interoperability Requirements

### 6.1 System Integration Requirements

<prompt: What integration capabilities and interfaces are required?>

**API and Interface Requirements** {{for_each_integration}}
**{{integration_name}}**

- Integration Type: {{integration_type}}
- Interface Protocol: {{interface_protocol}}
- Data Format Requirements: {{data_format}}
- Authentication Requirements: {{integration_auth}}
- Error Handling and Recovery: {{integration_error_handling}}
- Performance Requirements: {{integration_performance}} {{end_for_each}}

**Enterprise System Integration**

- Enterprise Service Bus (ESB) Requirements: {{esb_requirements}}
- Message Queue and Broker Needs: {{message_queue_requirements}}
- Event-Driven Architecture Support: {{event_driven_requirements}}
- Workflow and Orchestration: {{workflow_requirements}}
- Legacy System Integration: {{legacy_integration}}

### 6.2 Standards and Protocol Compliance

<prompt: What technical standards and protocols must be supported?>

**Technical Standards Compliance** {{for_each_standard}} **{{standard_name}}**

- Standard Requirements: {{standard_requirements}}
- Compliance Level: {{compliance_level}}
- Implementation Guidelines: {{implementation_guidelines}}
- Testing and Validation: {{validation_requirements}}
- Certification Needs: {{certification_requirements}} {{end_for_each}}

**Protocol and Format Support**

- Communication Protocols: {{communication_protocols}}
- Data Format Standards: {{data_format_standards}}
- Encoding and Character Set Support: {{encoding_requirements}}
- Compression and Optimization: {{compression_requirements}}
- Version Compatibility: {{version_compatibility}}

## 7. Monitoring and Observability Requirements

### 7.1 System Monitoring and Health Requirements

<prompt: What monitoring and observability capabilities are needed?>

**System Health Monitoring**

- Infrastructure Monitoring: {{infrastructure_monitoring}}
- Application Performance Monitoring (APM): {{apm_requirements}}
- Database Performance Monitoring: {{database_monitoring}}
- Network and Connectivity Monitoring: {{network_monitoring}}
- Security Monitoring and SIEM: {{security_monitoring}}

**Observability and Diagnostics** {{for_each_observability_area}}
**{{observability_area}}**

- Monitoring Requirements: {{monitoring_requirements}}
- Alerting and Notification: {{alerting_requirements}}
- Logging and Audit Trail: {{logging_requirements}}
- Metrics and KPI Tracking: {{metrics_requirements}}
- Troubleshooting Support: {{troubleshooting_support}} {{end_for_each}}

### 7.2 Alerting and Notification Requirements

<prompt: What alerting and notification capabilities are required?>

**Alert Configuration and Management** {{for_each_alert_type}}
**{{alert_type}}**

- Alert Conditions: {{alert_conditions}}
- Threshold Configuration: {{threshold_configuration}}
- Escalation Procedures: {{escalation_procedures}}
- Notification Methods: {{notification_methods}}
- Response and Resolution: {{response_requirements}} {{end_for_each}}

**Monitoring Dashboard Requirements**

- Operations Dashboard Needs: {{operations_dashboard}}
- Executive Dashboard Requirements: {{executive_dashboard}}
- Real-Time Monitoring Displays: {{realtime_monitoring}}
- Historical Analysis and Reporting: {{historical_analysis}}
- Custom Dashboard Creation: {{custom_dashboard_requirements}}

## 8. Deployment and DevOps Requirements

### 8.1 Deployment Architecture and Strategy

<prompt: What deployment capabilities and strategies are required?>

**Deployment Environment Requirements** {{for_each_environment}}
**{{environment_name}}**

- Environment Configuration: {{environment_configuration}}
- Deployment Method: {{deployment_method}}
- Infrastructure Requirements: {{infrastructure_requirements}}
- Security Configuration: {{security_configuration}}
- Testing and Validation: {{testing_requirements}} {{end_for_each}}

**CI/CD Pipeline Requirements**

- Source Code Management: {{source_code_management}}
- Build and Compilation Requirements: {{build_requirements}}
- Testing and Quality Assurance: {{testing_pipeline}}
- Deployment Automation: {{deployment_automation}}
- Release Management: {{release_management}}

### 8.2 Operational Requirements

<prompt: What operational capabilities are needed for ongoing system
management?>

**Backup and Recovery Requirements**

- Backup Strategy and Frequency: {{backup_strategy}}
- Recovery Time Objectives (RTO): {{rto_requirements}}
- Recovery Point Objectives (RPO): {{rpo_requirements}}
- Disaster Recovery Procedures: {{disaster_recovery}}
- Business Continuity Planning: {{business_continuity}}

**Maintenance and Support Requirements**

- System Maintenance Windows: {{maintenance_windows}}
- Update and Patch Management: {{patch_management}}
- Capacity Management: {{capacity_management}}
- Performance Tuning: {{performance_tuning}}
- Technical Support Requirements: {{support_requirements}}

## 9. Testing and Quality Assurance Requirements

### 9.1 Testing Strategy and Requirements

<prompt: What testing capabilities and strategies are required?>

**Testing Framework Requirements** {{for_each_testing_type}}
**{{testing_type}}**

- Testing Scope and Coverage: {{testing_scope}}
- Testing Tools and Frameworks: {{testing_tools}}
- Automation Requirements: {{automation_requirements}}
- Performance and Load Testing: {{performance_testing}}
- Security Testing: {{security_testing}} {{end_for_each}}

**Quality Assurance Process**

- Code Quality Standards: {{code_quality_standards}}
- Review and Approval Process: {{review_process}}
- Defect Management: {{defect_management}}
- Quality Metrics and KPIs: {{quality_metrics}}
- Continuous Improvement: {{continuous_improvement}}

### 9.2 Validation and Acceptance Criteria

<prompt: What validation and acceptance criteria must be met?>

**Acceptance Testing Requirements** {{for_each_acceptance_category}}
**{{acceptance_category}}**

- Acceptance Criteria: {{acceptance_criteria}}
- Testing Procedures: {{testing_procedures}}
- Success Metrics: {{success_metrics}}
- Stakeholder Approval: {{stakeholder_approval}}
- Sign-off Requirements: {{signoff_requirements}} {{end_for_each}}

**Performance Validation**

- Performance Benchmarks: {{performance_benchmarks}}
- Load Testing Requirements: {{load_testing}}
- Stress Testing Specifications: {{stress_testing}}
- Scalability Validation: {{scalability_validation}}
- User Acceptance Testing: {{user_acceptance_testing}}

## 10. Technical Requirements Validation and Approval

### 10.1 Requirements Review and Validation

<prompt: How will technical requirements be reviewed and validated?>

**Technical Review Process**

- Architecture Review: {{architecture_review}}
- Security Review: {{security_review}}
- Performance Review: {{performance_review}}
- Integration Review: {{integration_review}}
- Compliance Review: {{compliance_review}}

**Stakeholder Validation and Approval** {{for_each_stakeholder}}
**{{stakeholder_name}}**

- Review Responsibilities: {{review_responsibilities}}
- Approval Authority: {{approval_authority}}
- Review Timeline: {{review_timeline}}
- Approval Criteria: {{approval_criteria}}
- Sign-off Requirements: {{signoff_requirements}} {{end_for_each}}

### 10.2 Requirements Traceability and Management

<prompt: How will requirements be managed and traced throughout
implementation?>

**Requirements Management Framework**

- Requirements Documentation: {{requirements_documentation}}
- Change Management Process: {{change_management}}
- Version Control and History: {{version_control}}
- Traceability Matrix: {{traceability_matrix}}
- Impact Analysis Procedures: {{impact_analysis}}

**Implementation Planning Integration**

- Development Planning: {{development_planning}}
- Resource Allocation: {{resource_allocation}}
- Timeline and Milestone Planning: {{timeline_planning}}
- Risk Management Integration: {{risk_management}}
- Quality Assurance Planning: {{qa_planning}}

## Metadata

- Template Version: 1.0
- Last Updated: 2025-05-21
- Use Case: Technical Requirements Analysis for Data and Analytics Projects
- Applicable Technologies: Data Warehousing, Business Intelligence, Analytics
  Platforms, Cloud Infrastructure
