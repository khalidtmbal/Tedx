TEDxAl Neelain University — THE CONFLUENCE
Website + Organizer Command Center / Preview build 0.2

WHAT'S INCLUDED
- index.html: redesigned public landing page (The Confluence concept)
- about.html: event story and editorial principles
- register.html: interest registration form
- admin.html: organizer Command Center with 11 workspaces
- styles.css / script.js: public website styles and interactions
- admin.css / admin.js: organizer dashboard styles and preview data workflows

DESIGN DIRECTION
The Confluence takes visual inspiration from the meeting of the Blue Nile and White Nile in Khartoum. The public experience uses dark editorial layouts, river/current-inspired geometry, restrained TEDx red, warm paper tones, and strong typography. Replace the sample image with approved Al Neelain University / Khartoum photography before launch. Do not modify the official TEDx logo or imply TED endorsement beyond the license.

PREVIEW
Open index.html for the public site.
Open admin.html for the organizer Command Center.
No build tools are required. Google Fonts and the sample remote image require internet access.

COMMAND CENTER MODULES
Overview, registration CRM, speaker pipeline, programme builder, team/tasks, budget/finance, partner pipeline, volunteer desk, marketing calendar, logistics, and risks/decisions.

IMPORTANT: PREVIEW MODE, NOT PRODUCTION
This build is a functional front-end prototype. Dashboard workspaces support adding entries, toggling tasks, calculating budget totals/readiness, searching registrations and exporting CSV. Dashboard records and public form submissions are stored in browser localStorage. They are NOT shared between devices, browsers or team members. The dashboard currently has no login/authentication and must not be exposed as a live admin portal or used for confidential event data.

EXISTING SUPABASE REGISTRATION DATABASE
The previous project context describes an existing public.attendees table with fields such as id, registration_number, full_name, email, phone, affiliation, interest, consent_to_updates, status and created_at. This prototype deliberately does not connect directly to Supabase because no project URL, server-side API, or authentication setup was supplied. Do not put a Supabase service-role key in browser JavaScript.

PRODUCTION CONNECTION PLAN
1. Keep the existing attendees table and its constraints; do not recreate or overwrite it.
2. Add a secure server-side API (or Supabase Edge Functions) for public interest submissions and organizer reads/exports.
3. Use Supabase Auth for organizer sign-in and role-based access. Restrict organizer data through RLS policies. Keep service-role credentials server-side only.
4. Connect the public form POST to the server-side endpoint; map the submitted values to the existing enum/text conventions and return a safe confirmation.
5. Connect the dashboard CRM to an authenticated endpoint. Never expose attendee PII through an unrestricted public SELECT policy.
6. Persist organizer modules in database tables (tasks, speakers, programme_items, budget_lines, partners, volunteers, campaigns, logistics_items, risks, decisions, audit_logs) with created_by, timestamps and appropriate access controls.
7. Add audit logging, backups, privacy notice/retention rules, and test RLS using separate anonymous and organizer accounts.
8. Add real login, password reset, and server-side authorization before deployment.

RECOMMENDED DATABASE SHAPE
- event_tasks(id, title, owner, due_at, priority, status, created_by, created_at, updated_at)
- speakers(id, full_name, idea, contact, pipeline_status, notes, created_by, created_at)
- programme_items(id, starts_at, title, segment_type, sort_order)
- budget_lines(id, name, category, estimate_sdg, actual_sdg, notes)
- partners(id, organization, category, contact, pipeline_status, notes)
- volunteers(id, full_name, role, availability, contact, status)
- campaigns(id, title, channel, publish_at, status, owner)
- logistics_items(id, title, owner, due_at, status, notes)
- risk_register(id, title, severity, mitigation, status, owner)
- decisions(id, title, rationale, decided_by, decided_at)
- audit_logs(id, actor_id, action, entity, entity_id, created_at)

BEFORE PUBLISHING
- Confirm the TEDx license and naming/branding requirements with TED.
- Confirm date, venue, programme, contact channels and privacy notice.
- Replace sample photography with approved local imagery and verify image rights.
- Connect and test the secure backend and authentication; remove all preview-mode messaging only after production integration is complete.
- Test mobile layout, keyboard navigation, accessibility, data validation, duplicate emails, error states and all RLS policies.
