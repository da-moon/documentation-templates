# Comprehensive Meeting Documentation Template

## Template Usage Instructions

This template helps AI systems create comprehensive meeting documentation:
- Use {{placeholder}} syntax for variable information
- Follow <prompt: question> format for gathering specific details
- Use {{for_each}} loops for repeatable sections
- [Optional] sections can be included based on meeting needs

## 1. Meeting Overview

### 1.1 Basic Information
<prompt: What are the fundamental details of this meeting?>
- Meeting Title: {{meeting_title}}
- Date: {{meeting_date}}
- Time: {{start_time}} - {{end_time}}
- Location/Format: {{meeting_location}}
- Meeting Type: {{meeting_type}}
- Facilitator: {{facilitator_name}}
- Note Taker: {{note_taker_name}}

### 1.2 Meeting Purpose
<prompt: What is the purpose of this meeting?>
- Primary Objective: {{primary_objective}}
- Expected Outcomes: {{expected_outcomes}}
- Context: {{meeting_context}}

## 2. Attendance

### 2.1 Required Attendees
<prompt: Who were the required attendees?>
{{for_each_required_attendee}}
- Name: {{attendee_name}}
  - Role: {{attendee_role}}
  - Department: {{department}}
  - Attendance Status: {{attendance_status}}
  - Contact Information: {{contact_info}}
{{end_for_each}}

### 2.2 Optional Attendees [Optional]
<prompt: Who were the optional attendees?>
{{for_each_optional_attendee}}
- Name: {{attendee_name}}
  - Role: {{attendee_role}}
  - Department: {{department}}
  - Attendance Status: {{attendance_status}}
  - Contact Information: {{contact_info}}
{{end_for_each}}

## 3. Agenda and Discussion

### 3.1 Agenda Overview
<prompt: What was the meeting agenda?>
{{for_each_agenda_item}}
- Topic: {{topic_title}}
  - Duration: {{allocated_time}}
  - Presenter: {{presenter_name}}
  - Objectives: {{topic_objectives}}
{{end_for_each}}

### 3.2 Discussion Details
<prompt: What was discussed for each agenda item?>
{{for_each_discussion_topic}}
#### {{topic_title}}
- Key Points:
{{for_each_key_point}}
  - {{point_description}}
{{end_for_each}}
- Decisions Made:
{{for_each_decision}}
  - {{decision_description}}
{{end_for_each}}
- Action Items:
{{for_each_action}}
  - {{action_description}}
{{end_for_each}}
- Questions Raised:
{{for_each_question}}
  - {{question_text}}
{{end_for_each}}
{{end_for_each}}

## 4. Key Decisions

### 4.1 Decision Log
<prompt: What decisions were made during the meeting?>
{{for_each_decision}}
- Decision ID: {{decision_id}}
  - Description: {{decision_description}}
  - Context: {{decision_context}}
  - Decision Maker: {{decision_maker}}
  - Date: {{decision_date}}
  - Impact: {{decision_impact}}
  - Implementation Plan: {{implementation_plan}}
{{end_for_each}}

## 5. Action Items

### 5.1 New Action Items
<prompt: What new action items were identified?>
{{for_each_action_item}}
- Action ID: {{action_id}}
  - Description: {{action_description}}
  - Owner: {{action_owner}}
  - Due Date: {{due_date}}
  - Priority: {{priority_level}}
  - Status: {{current_status}}
  - Dependencies: {{dependencies}}
  - Notes: {{additional_notes}}
{{end_for_each}}

### 5.2 Action Items Update [Optional]
<prompt: What updates are there on existing action items?>
{{for_each_existing_action}}
- Action ID: {{action_id}}
  - Status Update: {{status_update}}
  - Progress: {{progress_details}}
  - Blockers: {{blockers}}
  - Next Steps: {{next_steps}}
{{end_for_each}}

## 6. Issues and Risks

### 6.1 Identified Issues/Risks
<prompt: What issues or risks were identified?>
{{for_each_issue_risk}}
- ID: {{issue_risk_id}}
  - Type: {{issue_or_risk}}
  - Description: {{description}}
  - Impact: {{impact_level}}
  - Owner: {{owner}}
  - Status: {{current_status}}
  - Mitigation Plan: {{mitigation_plan}}
{{end_for_each}}

## 7. Next Steps

### 7.1 Immediate Actions
<prompt: What immediate actions need to be taken?>
{{for_each_immediate_action}}
- Action: {{action_description}}
  - Owner: {{action_owner}}
  - Timeline: {{completion_timeline}}
  - Dependencies: {{dependencies}}
{{end_for_each}}

### 7.2 Follow-up Meetings
<prompt: What follow-up meetings are planned?>
{{for_each_followup}}
- Meeting: {{meeting_title}}
  - Purpose: {{meeting_purpose}}
  - Target Date: {{target_date}}
  - Required Attendees: {{required_attendees}}
{{end_for_each}}

## 8. Additional Information

### 8.1 Reference Materials
<prompt: What materials were referenced or shared?>
{{for_each_material}}
- Material: {{material_name}}
  - Type: {{material_type}}
  - Location: {{material_location}}
  - Purpose: {{material_purpose}}
{{end_for_each}}

### 8.2 Parking Lot Items [Optional]
<prompt: What items were deferred for future discussion?>
{{for_each_parked_item}}
- Item: {{item_description}}
  - Reason Parked: {{reason}}
  - Follow-up Plan: {{followup_plan}}
{{end_for_each}}

## 9. Approval Section

### 9.1 Document Approval
<prompt: Who needs to approve these meeting notes?>
{{for_each_approver}}
- Role: {{approver_role}}
  - Name: {{approver_name}}
  - Status: {{approval_status}}
  - Date: {{approval_date}}
{{end_for_each}}

## Metadata
- Template Version: 1.0
- Last Updated: 2025-05-21
- Generated By: AI Documentation Assistant

## Appendices [Optional]
- Meeting Recording: {{recording_link}}
- Presentation Materials: {{presentation_materials}}
- Supporting Documents: {{supporting_docs}}
