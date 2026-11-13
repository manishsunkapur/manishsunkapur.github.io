# Er. Manish Sunkapur — Product Manager Portfolio

**Live portfolio:** [manishsunkapur.github.io](https://manishsunkapur.github.io/)  
**Try the Quality Intelligence prototype:** [Open the demo](https://defect-detective-lab.lovable.app/)  
**View prototype analytics:** [Amplitude chart · test data](https://app.amplitude.com/analytics/share/96bb9312949b495fb4632b8e00936a27)

Product work across industrial SaaS, manufacturing workflows and AI-enabled products. This static site uses HTML, CSS and JavaScript; it has no paid hosting, build step or tracking code.

## Project pages and prototypes

- **Quality Intelligence** — [case study](https://manishsunkapur.github.io/#case-study) · [prototype](https://defect-detective-lab.lovable.app/).
- **LaunchLane** — [case study](https://manishsunkapur.github.io/launchlane/case-study.html) · [prototype](https://manishsunkapur.github.io/launchlane/).
- **Amtech APB · Downtime Recovery** — [case study](https://manishsunkapur.github.io/amtech-apb/case-study.html) · [prototype](https://manishsunkapur.github.io/amtech-apb/prototype/) · [full PM artifacts](https://github.com/manishsunkapur/product-management-portfolio/tree/main/projects/amtech-apb-scheduling/docs).

## Quick Reference Table: Step-by-Step Summary

| Order | PM Stage | Key Deliverables | Best Frameworks |
| --- | --- | --- | --- |
| 1 | Strategy | Quarterly goals, vision | OKRs, SMART |
| 2 | Discovery | Problem statement, user insights, pain points | JTBD, 5 Whys |
| 3 | Prioritization | Roadmap, MVP scope | RICE, MoSCoW |
| 4 | Documentation | PRD, success metrics | Opportunity Solution Tree |
| 5 | Prototyping | Wireframes, usability feedback | Design Thinking, HEART |
| 6 | Breakdown | Epics, user stories, acceptance criteria | INVEST, Given–When–Then |
| 7 | Delivery & Growth | Release readiness, instrumentation, analytics review | Scrum, AARRR* |

*Frameworks overlap in practice. Use AARRR where a growth question is relevant; operational B2B products also need task success, customer outcomes, and guardrail measures.*

## Quality Intelligence case study

- **Problem frame:** during downtime, help investigators identify the defect and find the correct approved report and parameter.
- **JTBD:** find and verify the right record faster without guessing or reducing accuracy.
- **Discovery:** Double Diamond to move from reported problem to a testable concept.
- **Objective:** draft SMART outcome; baseline, target, cohort and test window still need agreement.
- **Solution choice:** search first, one clue with optional filters, visible evidence and human confirmation; defer broad AI prediction.
- **Measures:** operational time to correct information; the user-stated 96% accuracy guardrail (definition to verify); workflow completion and drop-off; and necessary versus avoidable supervisor escalations.
- **Current Amplitude view:** seven-step prototype funnel from investigation start through search, results, record confirmation, report check and guidance. The last 30-day sample shows 5 test users starting and 1 reaching report check/guidance (20%). It counts unique users, not investigations or customers.
- **Instrumentation limits:** this is fictional prototype traffic, not customer engagement or an operator baseline. `investigation_id` exists in the event schema, but consistent use across every step is unverified. Sample timings are not operational task times; no dedicated supervisor-review event is currently in the funnel.
- **Release control:** independent proposal review and publishing, audit trail, rollback, and zero unapproved production mapping changes.

## Evidence boundary

The case study is an independent learning project. The prototype uses fictional records and reported, unverified inputs. It does not claim customer validation, live factory integration, measured time savings or production release. Report checking and supervisor support are prototype demonstrations; the role switch is not real access control. The Amplitude chart measures workflow progression, not repeat engagement or verified product outcomes.

## Files

- `index.html` — portfolio, project highlights, lifecycle quick reference, and Quality Intelligence case study.
- `amtech-apb/case-study.html` and `amtech-apb/prototype/index.html` — Amtech APB downtime recovery concept and clickable prototype.
- `assets/CV_Manish_Sunkapur.pdf` — downloadable CV.
- `assets/manish-sunkapur.jpg` — profile portrait.

GitHub Pages publishes the repository root. Keep personal details accurate and do not add private Jira/Notion content or confidential factory information.
