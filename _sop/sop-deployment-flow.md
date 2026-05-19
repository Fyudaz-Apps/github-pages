---
layout: default
title: Production Release & Deployment Flow
description: Standard operating procedure detailing steps for preparing, testing, and deploying changes to the production environment.
category: Deployment
author: Senior DevOps Engineer
last_updated: "2026-05-19"
---

# Production Release & Deployment Flow

This document details the standard operating procedure (SOP) for deploying software to our production environments. Adhering to this process ensures minimum downtime, high traceability, and robust rollback pathways.

## Pre-requisites
1. **Pass Staging Tests:** The release branch must pass all unit, integration, and user acceptance tests (UAT) in the staging environment.
2. **Pull Request Approval:** Code changes must be reviewed and approved by at least one Senior Engineer or Tech Lead.
3. **Change Control Approval:** A Change Request Ticket must be submitted and approved for any major releases.

---

## Deployment Steps

| Step | Owner | Action | Verification |
| :--- | :--- | :--- | :--- |
| **1. Freeze Branch** | Tech Lead | Lock the staging branch and cut a new release tag (e.g., `v2.4.0`). | Check GitHub tags list. |
| **2. Run Sync Actions** | DevOps | Trigger automated build pipelines. | Confirm GitHub Actions build returns a green status. |
| **3. Database Migration** | Lead DB Admin | Run pre-deployment database migrations in dry-run mode first, then apply. | Check migration tables for updated schema version. |
| **4. Deploy Code** | DevOps | Deploy artifacts/containers to production using rolling-update strategy. | Monitor CPU/Memory metrics and kubernetes pod health. |
| **5. Post-deploy Check** | QA Team | Conduct sanity tests on production endpoints. | Verify core user paths are functional and return 200 OK. |

---

## Rollback Procedure

If any critical errors or performance regressions are detected post-deployment (e.g., 5xx error rate > 1%):

1. **Initiate Rollback:** Run the automated rollback command:
   ```bash
   helm rollback main-application-release <previous_revision_number>
   ```
2. **Database Rollback:** If database migrations are backward-incompatible, execute the migration rollback script.
3. **Notify Stakeholders:** Update the DevOps slack channel and incident manager with status.
4. **Post-Mortem:** Document the incident details, root cause, and remediation steps in the portal's incident section.
