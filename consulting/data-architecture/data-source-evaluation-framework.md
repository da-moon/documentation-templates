# Data Source Evaluation Framework Template

## Template Usage Instructions

This template helps AI systems and data architects systematically evaluate data
sources for integration projects:

- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project needs

## 1. Data Source Profiling Overview

### 1.1 Basic Source Information

<prompt: What are the fundamental characteristics of each data source in your
project?>

{{for_each_data_source}} **Data Source: {{source_name}}**

- Source Type: {{source_type}} (SaaS API, Database, File Export, Streaming,
  etc.)
- Primary Business Purpose: {{business_purpose}}
- Data Domain: {{data_domain}} (Customer, Financial, Operational, etc.)
- Business Owner: {{business_owner}}
- Technical Owner: {{technical_owner}}
- Criticality Level: {{criticality_level}} (Mission-critical, Important,
  Nice-to-have)

**Access and Integration Characteristics**

- Authentication Method: {{auth_method}}
- Access Permissions Required: {{permission_requirements}}
- Rate Limiting Constraints: {{rate_limits}}
- API Stability and Versioning: {{api_stability}}
- Documentation Quality: {{documentation_quality}} {{end_for_each}}

### 1.2 Data Quality and Characteristics Assessment

<prompt: What are the quality and reliability characteristics of your data
sources?>

{{for_each_data_source}} **{{source_name}} - Data Quality Profile**

- Data Volume: {{data_volume}} (Records per day/week/month)
- Historical Data Availability: {{historical_scope}}
- Data Completeness: {{completeness_percentage}}
- Data Accuracy: {{accuracy_assessment}}
- Update Frequency: {{update_frequency}}
- Seasonal Patterns: {{seasonal_patterns}}
- Known Data Quality Issues: {{quality_issues}} {{end_for_each}}

## 2. Integration Complexity Analysis

### 2.1 Technical Integration Assessment

<prompt: What are the technical challenges and requirements for integrating
each data source?>

{{for_each_data_source}} **{{source_name}} - Integration Complexity**

**API and Connectivity Analysis**

- Integration Method: {{integration_method}} (REST API, GraphQL, Database
  connection, File transfer)
- Data Format: {{data_format}} (JSON, XML, CSV, Parquet, etc.)
- Pagination Strategy: {{pagination_method}}
- Filtering Capabilities: {{filtering_options}}
- Bulk Operation Support: {{bulk_operations}}

**Data Transformation Requirements**

- Schema Standardization Needs: {{schema_standardization}}
- Data Type Conversions Required: {{data_type_conversions}}
- Business Logic Transformation: {{business_logic_transforms}}
- Data Enrichment Requirements: {{enrichment_needs}}
- Deduplication and Cleanup Needs: {{cleanup_requirements}}

**Performance and Reliability Characteristics**

- Typical Response Times: {{response_times}}
- Peak Load Handling: {{peak_load_capacity}}
- Error Rate Patterns: {{error_patterns}}
- Downtime and Maintenance Windows: {{maintenance_patterns}}
- SLA and Availability Guarantees: {{sla_commitments}} {{end_for_each}}

### 2.2 Integration Risk Assessment

<prompt: What risks should be considered for each data source integration?>

{{for_each_data_source}} **{{source_name}} - Risk Analysis**

**Technical Risks**

- API Dependency Risk: {{api_dependency_risk}}
- Performance Degradation Risk: {{performance_risk}}
- Schema Change Risk: {{schema_change_risk}}
- Data Loss or Corruption Risk: {{data_loss_risk}}

**Business and Operational Risks**

- Data Privacy and Compliance Risk: {{privacy_risk}}
- Business Continuity Risk: {{continuity_risk}}
- Cost Escalation Risk: {{cost_risk}}
- Vendor Lock-in Risk: {{vendor_lockin_risk}}

**Mitigation Strategies**

- Primary Mitigation Approach: {{primary_mitigation}}
- Fallback and Recovery Procedures: {{fallback_procedures}}
- Monitoring and Early Warning Systems: {{monitoring_approach}}
- Business Continuity Plans: {{continuity_plans}} {{end_for_each}}

## 3. Cross-Source Integration Planning

### 3.1 Data Correlation and Mapping Strategy

<prompt: How will data from different sources be correlated and combined?>

**Identity Resolution Strategy**

- Primary Key Correlation Approach: {{primary_key_strategy}}
- Cross-Source Identity Mapping: {{identity_mapping_approach}}
- Fuzzy Matching Requirements: {{fuzzy_matching_needs}}
- Manual Mapping and Exception Handling: {{manual_mapping_process}}

**Temporal Correlation Strategy**

- Timestamp Normalization Approach: {{timestamp_normalization}}
- Time Zone Handling Strategy: {{timezone_strategy}}
- Event Sequencing and Ordering: {{event_sequencing}}
- Late-Arriving Data Handling: {{late_data_handling}}

### 3.2 Data Quality and Consistency Management

<prompt: How will data quality and consistency be maintained across sources?>

**Cross-Source Validation Strategy**

- Data Consistency Checks: {{consistency_validation}}
- Accuracy Validation Procedures: {{accuracy_validation}}
- Completeness Assessment Methods: {{completeness_assessment}}
- Timeliness Monitoring Approach: {{timeliness_monitoring}}

**Quality Alerting and Response**

- Quality Threshold Definitions: {{quality_thresholds}}
- Alerting and Escalation Procedures: {{alerting_procedures}}
- Data Quality Dashboard Requirements: {{quality_dashboard_needs}}
- Remediation and Correction Processes: {{remediation_processes}}

## 4. Performance and Scalability Planning

### 4.1 System Performance Requirements

<prompt: What are the performance requirements for your data integration
system?>

**Data Processing Performance Targets**

- Real-Time Processing Requirements: {{realtime_requirements}}
- Batch Processing Window Constraints: {{batch_windows}}
- Query Response Time Targets: {{query_response_targets}}
- Concurrent User Support Requirements: {{concurrent_user_needs}}

**Scalability and Growth Planning**

- Expected Data Volume Growth: {{volume_growth_projections}}
- User Growth and Access Pattern Changes: {{user_growth_patterns}}
- Processing Capacity Scaling Strategy: {{scaling_strategy}}
- Infrastructure Cost Management: {{cost_management_approach}}

### 4.2 Architecture and Infrastructure Planning

<prompt: What technical architecture will support your integration
requirements?>

**Data Pipeline Architecture**

- ETL/ELT Processing Framework: {{processing_framework}}
- Real-Time vs Batch Processing Strategy: {{processing_strategy}}
- Data Storage and Persistence Approach: {{storage_approach}}
- Caching and Performance Optimization: {{caching_strategy}}

**Infrastructure and Platform Requirements**

- Cloud vs On-Premise Strategy: {{deployment_strategy}}
- Containerization and Orchestration Needs: {{containerization_approach}}
- Monitoring and Observability Requirements: {{monitoring_requirements}}
- Disaster Recovery and Business Continuity: {{disaster_recovery_plans}}

## 5. Implementation Planning and Sequencing

### 5.1 Integration Prioritization Strategy

<prompt: What is the optimal sequence for implementing your data source
integrations?>

**Priority Assessment Criteria**

- Business Value and Impact Scoring: {{business_value_scoring}}
- Technical Complexity Assessment: {{complexity_assessment}}
- Risk Level Evaluation: {{risk_evaluation}}
- Resource Requirement Analysis: {{resource_analysis}}

**Implementation Sequence Planning** {{for_each_implementation_phase}} **Phase
{{phase_number}}: {{phase_name}} ({{phase_duration}})**

- Primary Data Sources: {{phase_data_sources}}
- Key Deliverables: {{phase_deliverables}}
- Success Criteria: {{phase_success_criteria}}
- Resource Requirements: {{phase_resources}}
- Dependencies and Risks: {{phase_dependencies}} {{end_for_each}}

### 5.2 Success Measurement and Validation

<prompt: How will you measure the success of your data source integrations?>

**Technical Success Metrics**

- Data Pipeline Reliability: {{pipeline_reliability_targets}}
- Data Quality Scores: {{quality_score_targets}}
- Performance Benchmarks: {{performance_benchmarks}}
- System Availability Targets: {{availability_targets}}

**Business Success Metrics**

- User Adoption and Satisfaction: {{adoption_metrics}}
- Decision Support Effectiveness: {{decision_support_metrics}}
- Business Process Improvement: {{process_improvement_metrics}}
- Cost Efficiency and ROI: {{cost_efficiency_metrics}}

## Metadata

- Template Version: 1.0
- Last Updated: 2025-05-21
- Use Case: Data Architecture and Integration Projects
- Applicable Technologies: API Integration, ETL/ELT, Data Warehousing, Business
  Intelligence
