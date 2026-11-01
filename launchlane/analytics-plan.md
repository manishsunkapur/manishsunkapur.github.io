# LaunchLane: Product Analytics Plan

**Status:** Draft for the independent SaaS portfolio prototype. Product metrics are hypotheses until validated with representative users. Seeded launch records are fictional and are never sent to Amplitude as user activity.

## Product frame
- **Product:** Shared onboarding workspace for small B2B SaaS vendors and their business customers.
- **Primary user:** Implementation lead coordinating a customer launch.
- **Secondary user:** Customer administrator completing setup tasks.
- **Problem hypothesis:** Work is coordinated across messages and documents, leaving both sides unsure of the next action and delaying first value.
- **MVP:** Create a launch from a template, assign and complete setup milestones, preview a customer invite, report and resolve blockers, and view progress.
- **Out of scope:** AI recommendations, real invitations, production access control, integrations, and claims of customer validation.

## Metric definitions
| Measure | Draft definition | Decision it supports |
|---|---|---|
| Activation within 14 days | Eligible launches that reach the first-value milestone within 14 days divided by launches whose full 14-day observation window has elapsed | Whether onboarding gets customers to value |
| Median time to first value | Median elapsed time from launch_created to first_value_reached for activated launches; report non-activated launches separately | Where onboarding takes too long |
| Invite acceptance | Launches with invite_accepted divided by launches with customer_invited | Whether the customer handoff works |
| Milestone completion | Distinct eligible milestones completed divided by distinct eligible milestones viewed | Which setup steps cause friction |
| Blocked-launch rate | Launches with at least one blocker_reported divided by launches started | How often progress is blocked |
| Blocker resolution time | Median time from blocker_reported to blocker_resolved | Whether reported blockers get cleared |
| Guardrails | Reopened milestones and access/control incidents, reviewed alongside activation | Prevent speed gains from weakening quality or trust |

Do not count a launch as a 14-day activation failure before its full observation window passes. Confirm the first-value task with users before treating this as a committed north-star metric.

## Event taxonomy
The public portfolio demo measures visitor interactions only after explicit opt-in. The Browser SDK loads only after consent; autocapture, session replay, and IP-address collection are disabled. If a visitor declines, the SDK does not load. Consent can be revoked under Privacy.

Common properties: environment=portfolio_demo; is_demo_data=true; persona=implementation_lead or customer_admin. The SDK uses an anonymous browser device identity. Do not send account names, emails, blocker text, launch notes, or other typed free text. Events describe demo activity, not customers or product adoption.

| Event | Trigger | Properties |
|---|---|---|
| demo_session_started | Start analytics after consent | environment, is_demo_data, persona |
| demo_session_ended | Leave page after an opted-in session | duration_seconds |
| workspace_page_viewed | Open app or select Overview, Launches, or Insights | page |
| launch_created | Create a fictional launch | launch_id, template_id |
| launch_viewed | Open a launch | launch_id |
| milestone_viewed | Open a launch or complete a step that reveals the next incomplete step | launch_id, milestone_id, step_order |
| milestone_completed | Mark a step complete | launch_id, milestone_id, step_order, step_duration_seconds |
| first_value_reached | Complete the first-workflow step | launch_id, milestone_id, time_to_value_seconds when available in this browser session |
| blocker_reported / blocker_resolved | Report or resolve a demo blocker | launch_id, blocker_category |
| invite_previewed / invite_accepted | Preview or accept the simulated invite | launch_id, common persona property |
| persona_preview_changed | Change the visual-only role preview | common persona property |

## Private Amplitude views
1. **Activation funnel:** launch_created -> milestone_completed for step 4 (first workflow); report only portfolio-demo sessions and label the chart as demo behavior.
2. **Milestone progression:** milestone_viewed -> milestone_completed by milestone_id/step_order. Diagnose drop-off; step counts are directional while volume is small.
3. **Time to value:** time from launch_created to first_value_reached; inspect time_to_value_seconds only when the same-browser duration is present. Separate sessions without completion.
4. **Blocker handling:** blocker_reported -> blocker_resolved by blocker_category.
5. **Invite handoff:** invite_previewed -> invite_accepted, broken down by the visual-only persona.

Keep all LaunchLane charts private. Do not describe portfolio visitor behavior as real customer outcomes or use the illustrative in-product chart as measured data.

## Implementation gate
The static GitHub Pages prototype has no backend, real accounts, real email, or enforced access control. Sample records and in-app chart bars are fictional and never sent to Amplitude. Only opted-in events use environment=portfolio_demo and is_demo_data=true. This telemetry describes portfolio-demo exploration, not a production onboarding product.
