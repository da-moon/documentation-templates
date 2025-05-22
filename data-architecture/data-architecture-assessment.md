# Data Architecture Assessment Template

## Template Usage Instructions

This template guides AI systems in creating comprehensive data architecture
assessments:

- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on project complexity

## 1. Current State Architecture Analysis

### 1.1 Existing Infrastructure Assessment

<prompt: What is the current state of data infrastructure and platforms?>

**Data Platform Inventory**

- Primary Data Warehouse/Lake: {{primary_data_platform}}
- BI and Analytics Tools: {{bi_tools}}
- ETL/ELT Processing Platforms: {{etl_platforms}}
- Data Integration Solutions: {{integration_tools}}
- Monitoring and Governance Tools: {{governance_tools}}

**Infrastructure Configuration** {{for_each_platform}} **{{platform_name}}**

- Version and Edition: {{platform_version}}
- Hosting Environment: {{hosting_environment}}
- Resource Allocation: {{resource_allocation}}
- Performance Characteristics: {{performance_metrics}}
- Authentication and Security: {{security_configuration}}
- Current User Base: {{user_count}}
- Utilization Patterns: {{utilization_patterns}} {{end_for_each}}

### 1.2 Data Flow and Integration Assessment

<prompt: How does data currently flow through your organization's systems?>

**Current Data Architecture Patterns**

- Data Ingestion Methods: {{ingestion_methods}}
- Processing and Transformation Approach: {{processing_approach}}
- Storage and Persistence Strategy: {{storage_strategy}}
- Data Distribution and Access Patterns: {{distribution_patterns}}

**Integration Complexity Analysis** {{for_each_integration}}

- Source System: {{source_system}}
- Integration Method: {{integration_method}}
- Data Volume and Frequency: {{volume_frequency}}
- Transformation Complexity: {{transformation_complexity}}
- Quality and Reliability Issues: {{quality_issues}} {{end_for_each}}

### 1.3 Performance and Scalability Assessment

<prompt: What are the current performance characteristics and limitations?>

**System Performance Metrics**

- Query Response Times: {{query_response_times}}
- Data Processing Throughput: {{processing_throughput}}
- Concurrent User Capacity: {{concurrent_capacity}}
- Peak Load Handling: {{peak_load_performance}}
- Resource Utilization Patterns: {{resource_utilization}}

**Scalability Limitations and Constraints**

- Identified Performance Bottlenecks: {{performance_bottlenecks}}
- Scaling Constraints: {{scaling_constraints}}
- Capacity Planning Challenges: {{capacity_challenges}}
- Cost and Resource Limitations: {{cost_constraints}}

## 2. Business Requirements and Use Case Analysis

### 2.1 Stakeholder Needs Assessment

<prompt: What are the business requirements driving your data architecture
needs?>

**Primary Stakeholder Groups** {{for_each_stakeholder_group}}
**{{stakeholder_group}}**

- Primary Information Needs: {{information_needs}}
- Decision-Making Requirements: {{decision_requirements}}
- Performance Expectations: {{performance_expectations}}
- Access and Security Requirements: {{access_requirements}}
- Growth and Scaling Needs: {{scaling_needs}} {{end_for_each}}

**Business Use Case Requirements** {{for_each_use_case}} **{{use_case_name}}**

- Business Objective: {{business_objective}}
- Data Requirements: {{data_requirements}}
- Processing Requirements: {{processing_requirements}}
- Performance Requirements: {{performance_requirements}}
- Integration Dependencies: {{integration_dependencies}}
- Success Criteria: {{success_criteria}} {{end_for_each}}

### 2.2 Compliance and Governance Requirements

<prompt: What compliance and governance requirements affect your data
architecture?>

**Regulatory Compliance Requirements** {{for_each_regulation}}

- Regulation: {{regulation_name}}
- Data Protection Requirements: {{data_protection_requirements}}
- Access Control Requirements: {{access_control_requirements}}
- Audit and Reporting Requirements: {{audit_requirements}}
- Retention and Deletion Requirements: {{retention_requirements}}
  {{end_for_each}}

**Data Governance Requirements**

- Data Quality Standards: {{quality_standards}}
- Metadata Management Needs: {{metadata_requirements}}
- Data Lineage and Provenance: {{lineage_requirements}}
- Change Management Procedures: {{change_management}}

## 3. Technical Architecture Recommendations

### 3.1 Target Architecture Design

<prompt: What is the recommended target architecture for your data platform?>

**Architectural Patterns and Approach**

- Overall Architecture Pattern: {{architecture_pattern}} (Lambda, Kappa,
  Medallion, etc.)
- Data Processing Strategy: {{processing_strategy}} (Batch, Stream, Hybrid)
- Storage Architecture: {{storage_architecture}} (Data Lake, Data Warehouse,
  Lakehouse)
- Integration Architecture: {{integration_architecture}} (Hub-and-spoke,
  Point-to-point, Event-driven)

**Technology Stack Recommendations** {{for_each_layer}} **{{layer_name}}
Layer**

- Recommended Technology: {{recommended_technology}}
- Alternative Options: {{alternative_options}}
- Selection Rationale: {{selection_rationale}}
- Implementation Considerations: {{implementation_considerations}}
- Integration Requirements: {{integration_requirements}} {{end_for_each}}

### 3.2 Data Processing and Pipeline Design

<prompt: How should data processing and pipelines be designed?>

**Data Pipeline Architecture**

- Ingestion Layer Design: {{ingestion_design}}
- Processing Layer Design: {{processing_design}}
- Storage Layer Design: {{storage_design}}
- Serving Layer Design: {{serving_design}}

**Processing Framework Recommendations** {{for_each_processing_type}}
**{{processing_type}} Processing**

- Recommended Framework: {{processing_framework}}
- Use Cases: {{processing_use_cases}}
- Performance Characteristics: {{processing_performance}}
- Scalability Considerations: {{processing_scalability}}
- Resource Requirements: {{processing_resources}} {{end_for_each}}

### 3.3 Security and Governance Architecture

<prompt: How should security and governance be implemented in the
architecture?>

**Security Architecture Design**

- Authentication and Authorization Strategy: {{auth_strategy}}
- Data Encryption Strategy: {{encryption_strategy}}
- Network Security Approach: {{network_security}}
- Access Control Implementation: {{access_control}}

**Governance Framework Implementation**

- Data Quality Monitoring: {{quality_monitoring}}
- Metadata Management Strategy: {{metadata_strategy}}
- Data Lineage Implementation: {{lineage_implementation}}
- Compliance Monitoring: {{compliance_monitoring}}

## 4. Implementation Strategy and Roadmap

### 4.1 Migration and Implementation Planning

<prompt: What is the recommended approach for implementing the target
architecture?>

**Implementation Phases** {{for_each_phase}} **Phase {{phase_number}}:
{{phase_name}} ({{phase_duration}})**

- Primary Objectives: {{phase_objectives}}
- Key Components: {{phase_components}}
- Success Criteria: {{phase_success_criteria}}
- Resource Requirements: {{phase_resources}}
- Risk Factors: {{phase_risks}}
- Dependencies: {{phase_dependencies}} {{end_for_each}}

**Migration Strategy**

- Data Migration Approach: {{migration_approach}}
- System Cutover Strategy: {{cutover_strategy}}
- Rollback and Recovery Plans: {{rollback_plans}}
- User Training and Change Management: {{change_management}}

### 4.2 Technology Selection and Evaluation

<prompt: What criteria should guide technology selection decisions?>

**Technology Evaluation Framework**

- Performance and Scalability Criteria: {{performance_criteria}}
- Cost and Licensing Considerations: {{cost_criteria}}
- Integration and Compatibility Requirements: {{integration_criteria}}
- Support and Community Factors: {{support_criteria}}
- Strategic and Long-term Considerations: {{strategic_criteria}}

**Recommended Technology Stack** {{for_each_technology_category}}
**{{technology_category}}**

_Option 1: {{option_1_name}}_

- Pros: {{option_1_pros}}
- Cons: {{option_1_cons}}
- Best Use Cases: {{option_1_use_cases}}
- Cost Implications: {{option_1_costs}}

_Option 2: {{option_2_name}}_

- Pros: {{option_2_pros}}
- Cons: {{option_2_cons}}
- Best Use Cases: {{option_2_use_cases}}
- Cost Implications: {{option_2_costs}}

_Recommendation: {{recommended_option}}_

- Rationale: {{recommendation_rationale}} {{end_for_each}}

## 5. Success Measurement and Validation

### 5.1 Success Criteria and KPIs

<prompt: How will the success of the new architecture be measured?>

**Technical Success Metrics**

- System Performance Improvements: {{performance_improvements}}
- Reliability and Availability Metrics: {{reliability_metrics}}
- Scalability and Capacity Utilization: {{scalability_metrics}}
- Cost Efficiency and Resource Optimization: {{cost_efficiency_metrics}}

**Business Success Metrics**

- User Adoption and Satisfaction: {{adoption_metrics}}
- Decision-Making Support and Quality: {{decision_support_metrics}}
- Business Process Improvement: {{process_improvement_metrics}}
- Time-to-Insight and Analytics Velocity: {{insight_velocity_metrics}}

### 5.2 Monitoring and Continuous Improvement

<prompt: How will the architecture be monitored and continuously improved?>

**Monitoring and Observability Strategy**

- System Health and Performance Monitoring: {{health_monitoring}}
- Data Quality and Pipeline Monitoring: {{quality_monitoring}}
- User Experience and Adoption Monitoring: {{user_monitoring}}
- Cost and Resource Utilization Monitoring: {{cost_monitoring}}

**Continuous Improvement Framework**

- Regular Architecture Reviews: {{architecture_reviews}}
- Performance Optimization Cycles: {{optimization_cycles}}
- Technology Evolution and Upgrade Planning: {{evolution_planning}}
- Stakeholder Feedback Integration: {{feedback_integration}}

## Metadata

- Template Version: 1.0
- Last Updated: 2025-05-21
- Use Case: Data Architecture Design and Assessment
- Applicable Technologies: Data Warehouses, Data Lakes, ETL/ELT, Business
  Intelligence, Analytics Platforms
