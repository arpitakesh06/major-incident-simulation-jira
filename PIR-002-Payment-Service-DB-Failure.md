# Post-Incident Review — PIR-002
## P1 — Payment Service Database Connection Failure

**Date of Incident:** 05-June-2025  
**Date of PIR:** 07-June-2025  
**Severity:** P1  
**Status:** Closed  
**Facilitated by:** Arpita Kesharwani  

---

## 1. Incident Summary
Payment service database became unreachable at 14:00 on 05-June-2025
due to connection pool exhaustion during peak traffic. All payment 
transactions failed during the outage window. Service was fully 
restored within 72 minutes.

---

## 2. Timeline

| Time | Event |
|------|-------|
| 14:00 | Monitoring alert fired — payment service DB unreachable |
| 14:02 | Incident logged in Jira as P1 — SUP-2 |
| 14:03 | Slack channel #incident-p1-payment-db opened |
| 14:05 | First stakeholder update sent |
| 14:10 | L2 DBA team engaged |
| 14:20 | Connection pool exhaustion identified as root cause |
| 14:25 | Stakeholder update sent — root cause identified |
| 14:50 | Connection pool size increased from 50 to 200 |
| 15:00 | Payment service restarted |
| 15:12 | Service fully restored — all-clear sent |
| 15:15 | Incident closed in Jira |

---

## 2. Impact
- **Users affected:** All users attempting payment transactions
- **Duration:** 72 minutes
- **Services affected:** Payment Service, Transaction Processing
- **Business impact:** All payment transactions failed during outage window

---

## 4. Root Cause
Database connection pool size was set too low for peak traffic volumes.
During high traffic period, all available connections were exhausted 
causing the payment service to be unable to connect to the database.

---

## 5. Contributing Factors
- Connection pool size not reviewed after traffic growth
- No alert configured for connection pool utilisation
- No load testing performed for peak traffic scenarios

---

## 6. What Went Well
- Incident detected quickly via monitoring
- DBA team engaged within 10 minutes
- Stakeholder updates sent every 15 minutes
- Root cause identified within 20 minutes

---

## 7. What Could Be Improved
- Connection pool alert should have been configured
- Pool size review should be part of regular capacity planning
- Load testing should be scheduled quarterly

---

## 8. Action Items

| Action Item | Owner | Deadline | Status |
|-------------|-------|----------|--------|
| Increase connection pool size permanently | DBA Team Lead | 26-June-2025 | Completed |
| Configure connection pool utilisation alert at 80% | Infrastructure Team | 20-June-2025 | Completed |
| Schedule quarterly load testing | QA Team Lead | 30-June-2025 | In Progress |
| Update DB connection failure runbook | Arpita Kesharwani | 22-June-2025 | Completed |

---

## 9. Lessons Learned
- Connection pool sizing must keep pace with traffic growth
- Proactive capacity planning prevents P1 incidents
- Load testing identifies bottlenecks before they cause outages
