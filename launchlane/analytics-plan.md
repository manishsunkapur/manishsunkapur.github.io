# LaunchLane: Product Analytics Plan

**Status:** Draft for the independent SaaS portfolio prototype. Problem and product metrics are hypotheses until validated with representative users. The prototype’s seeded launch records are fictional and must not be sent to Amplitude as if they were user activity.

## Product frame

- **Product:** LaunchLane, a shared onboarding workspace for small B2B SaaS vendors and their business customers.
- **Primary user:** implementation lead coordinating a customer launch.
- **Secondary user:** customer administrator completing setup tasks.
- **Problem hypothesis:** onboarding work is coordinated across messages and documents, leaving each side unsure of the next action and delaying first value.
- **MVP:** create a launch from a template, assign and complete setup milestones, invite a customer administrator, report/resolve blockers, and see launch progress.
- **Not in scope:** AI recommendations, real invitations, production access control, integrations, or claims of customer validation.

## Metric definitions

| Measure | Draft definition | Decision it supports |
|---|---|---|
| Activation within 14 days | Eligible launches that reach the first-value milestone within 14 days ÷ eligible launches whose full 14-day observation window has elapsed | Whether the onboarding flow gets customers to value |
| Median time to first value | Median elapsed time from `launch_created` to the first `first_value_reached` for activated launches; report non-activated launches separately | Where onboarding takes too long |
| Invite acceptance | Launches with `invite_accepted` ÷ launches with `customer_invited` | Whether the hand-off to the customer works |
| Milestone completion | Distinct eligible milestones completed ÷ distinct eligible milestones started | Which setup steps cause friction |
| Blocked-launch rate | Launches with at least one `blocker_reported` ÷ launches started | How often progress is blocked |
| Blocker resolution time | Median time from `blocker_reported` to `blocker_resolved` | Whether reported blockers get cleared |
| Guardrails | Reopened milestones and access/control incidents, reviewed alongside activation | Prevents optimizing speed at the expense of quality or trust |

Do not count a launch as a 14-day activation failure until its full observation window has passed. Confirm the exact “first value” task with users before treating it as a committed north-star metric.

## Event taxonomy

The public portfolio demo measures visitor interactions only after an explicit opt-in. The Browser SDK is loaded only after consent; autocapture, session replay, and IP-address property collection are disabled. If the visitor declines, no analytics script is loaded. Revoke by reopening Privacy and choosing Turn off.

Common properties: environment=portfolio_demo, is_demo_data=true, persona=implementation_lead or customer_admin. The SDK uses its anonymous browser device identity. Do not send account names, emails, blocker text, launch notes, or any other typed free text. Seed records are fictional. Events describe demo activity, not customers or adoption.

| Event | Trigger | Properties |
|---|---|---|
| demo_session_started / demo_session_ended | Start after consent / leave page | duration_seconds on end |
| workspace_page_viewed | Open the app after consent or select Overview, Launches, or Insights | page |
| launch_created | Create a fictional launch | launch_id, template_id |
| launch_viewed | Open a launch | launch_id |
| milestone_viewed | Open a launch with a next incomplete step | launch_id, milestone_id, step_order |
| milestone_completed | Mark a step complete | launch_id, milestone_id, step_order, step_duration_seconds |
| first_value_reached | Complete the first-workflow step | launch_id, milestone_id, time_to_value_seconds only for launches created in this browser session |
| blocker_reported / blocker_resolved | Report or resolve a demo blocker | launch_id, blocker_category |
| invite_previewed / invite_accepted | Preview or accept the simulated customer invite | launch_id; common persona property |
| persona_preview_changed | Change the visual-only role preview | common persona property |

## Amplitude views

After events arrive, create private views for: (1) demo entry to launch creation to first workflow; (2) milestone viewed-to-completed by step_order, to identify demo-flow abandonment; (3) step_duration_seconds and time_to_value_seconds distributions for launches created during a session; (4) blocker reported-to-resolved and simulated invite preview-to-acceptance. Label all charts as portfolio-demo behavior. Do not publish the chart link unless separately asked.

## Implementation gate

The app is a static GitHub Pages prototype at github-pages-source/launchlane/. It has no backend or real customer accounts. Local sample records and chart bars remain fictional; they are never ingested into Amplitude. The consent choice is stored in the visitor's browser. Amplitude receives only opted-in interaction events with environment=portfolio_demo and is_demo_data=true. This telemetry indicates how people explore the portfolio prototype, not whether a production onboarding product improves customer outcomes.