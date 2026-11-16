# 📚 BizRadar Insights Documentation

Welcome to the technical and product documentation for BizRadar Insights. This directory explains the application as it exists in source, including its React frontend, local analytics engines, Supabase integration, Edge Functions, database migrations, operational practices, and current limitations.

> **Important:** Several market/forecast calculations use mock, generated, or rule-based inputs. AI output and heuristic scores are not independently verified market research or financial advice.

## 🧭 Reading paths

### For users and product reviewers
1. [Overview](overview.md)
2. [Requirements and scope](requirements.md)
3. [Feature workflows](workflows.md)
4. [Data sources and limitations](data-sources.md)
5. [Analytics methodology](analytics-methodology.md)
6. [FAQ](faq.md)

### For frontend developers
1. [Installation](installation.md)
2. [Configuration](configuration.md)
3. [Architecture](architecture.md)
4. [Project structure](project-structure.md)
5. [Performance](performance.md)
6. [Accessibility](accessibility.md)
7. [Testing](testing.md)

### For Supabase/backend developers
1. [Supabase setup](supabase-setup.md)
2. [Database model](database.md)
3. [API and Edge Functions](api.md)
4. [Security review](security-review.md)
5. [Threat model](threat-model.md)
6. [Operations](operations.md)
7. [Backup and recovery](backup-recovery.md)

### For maintainers
1. [Contributing](../CONTRIBUTING.md)
2. [Security policy](../SECURITY.md)
3. [Deployment](deployment.md)
4. [Troubleshooting](troubleshooting.md)
5. [Technical debt](../TECHNICAL_DEBT.md)
6. [Roadmap](../ROADMAP.md)
7. [Changelog](../CHANGELOG.md)

## 📖 Complete guide index

| Document | Contents |
|---|---|
| [Overview](overview.md) | Product purpose, users, scope and constraints |
| [Requirements](requirements.md) | Functional, quality, safety and acceptance requirements |
| [Architecture](architecture.md) | Browser application, module boundaries, integrations and data flow |
| [Project structure](project-structure.md) | Directory map and file responsibilities |
| [Installation](installation.md) | Prerequisites and clean local setup |
| [Configuration](configuration.md) | Environment variables and secret boundaries |
| [Supabase setup](supabase-setup.md) | Project, Auth, migrations, Edge Functions, secrets and RLS |
| [Database](database.md) | Migration-derived entity overview and access expectations |
| [API and Edge Functions](api.md) | Edge Function behavior, methods, auth and response shapes |
| [Analytics methodology](analytics-methodology.md) | BizScore, risk, competitor, finance and forecast logic |
| [Data sources](data-sources.md) | Mock data, synthetic values, geocoding and external providers |
| [Workflows](workflows.md) | User journeys and process diagrams |
| [Testing](testing.md) | Automated checks and manual scenario matrix |
| [Accessibility](accessibility.md) | WCAG-oriented checklist and test evidence |
| [Performance](performance.md) | React, data, map and chart optimization |
| [Security review](security-review.md) | Concrete source-observed findings |
| [Threat model](threat-model.md) | Data assets, attack surface and trust boundaries |
| [Privacy](privacy.md) | Data minimization, user records and retention |
| [Deployment](deployment.md) | Frontend and Supabase deployment steps |
| [Operations](operations.md) | Monitoring, logs, maintenance and incident response |
| [Backup and recovery](backup-recovery.md) | Database backup and restoration |
| [Troubleshooting](troubleshooting.md) | Known setup and runtime failures |
| [FAQ](faq.md) | Common questions |
| [Glossary](glossary.md) | Project-specific terms and metrics |

## 🗺️ Diagrams and templates

- [Diagram index](diagrams/README.md)
- [Architecture context](diagrams/architecture-context.mmd)
- [Application journey](diagrams/product-journey.mmd)
- [Analysis pipeline](diagrams/analysis-pipeline.mmd)
- [Authentication and persistence](diagrams/auth-and-data.mmd)
- [Template index](templates/README.md)
- [Architecture decision record](templates/adr.md)
- [Test plan/report](templates/test-plan.md)
- [Security finding](templates/security-finding.md)
- [Data source register](templates/data-source-register.md)
- [Release checklist](templates/release-checklist.md)
- [Incident report](templates/incident-report.md)
- [Feature proposal](templates/feature-proposal.md)

## ✅ Evidence and documentation policy

Claims should be classified as one of:
- **Implemented:** Visible in current checked-in code.
- **Configured:** Requires external project settings, secrets, provider credentials, or Supabase dashboard configuration.
- **Mock/rule-based:** Generated locally from deterministic rules or random variation.
- **Proposed:** Roadmap or future design only.
- **Unverified:** Not tested in a live environment or not confirmed from source.

A clean build does not prove live integration behavior. A migration file does not prove that the remote Supabase project has applied it. A public publishable key is not a substitute for database authorization. These distinctions should remain explicit in future changes.
