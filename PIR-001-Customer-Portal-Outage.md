# Post-Incident Review — PIR-001
## P1 — Customer Portal Application Outage

**Date of Incident:** 01-June-2025  
**Date of PIR:** 03-June-2025  
**Severity:** P1  
**Status:** Closed  
**Facilitated by:** Arpita Kesharwani  

---

## 1. Incident Summary
The customer portal became completely unavailable at 09:00 on 01-June-2025. 
Multiple users were unable to access the portal. The incident was resolved 
within 47 minutes with full service restoration confirmed at 09:47.

---

## 2. Timeline

| Time | Event |
|------|-------|
| 09:00 | Monitoring alert fired — customer portal unreachable |
| 09:02 | Incident logged in Jira as P1 — SUP-1 |
| 09:03 | Slack channel #incident-p1-portal-outage opened |
| 09:05 | First stakeholder update sent |
| 09:08 | L2 application team engaged |
| 09:15 | Memory leak identified as root cause |
| 09:20 | Stakeholder update sent — root cause identified |
| 09:40 | Application server restarted |
| 09:47 | Service fully restored — all-clear sent |
| 09:50 | Incident closed in Jira |

---

## 3. Impact
- **Users affected:** All customer portal users
- **Duration:** 47 minutes
- **Services affected:** Customer Portal
- **Business impact:** Users unable to access portal during outage window

---

## 4. Root Cause
Memory leak in application code caused server memory to reach 100% 
causing the application server to crash. No memory monitoring alert 
was configured to provide early warning.

---

## 5. Contributing Factors
- No memory usage alert configured below 100%
- No automated restart policy on memory exhaustion
- Runbook for application server crash not updated

---

## 6. What Went Well
- Incident detected quickly via monitoring
- Resolver team engaged within 8 minutes
- Stakeholder updates sent every 15 minutes
- Service restored within 47 minutes — within P1 SLA

---

## 7. What Could Be Improved
- Memory monitoring alert should have fired earlier
- Runbook needed updating for this scenario
- Escalation to L2 could have been faster

---

## 8. Action Items

| Action Item | Owner | Deadline | Status |
|-------------|-------|----------|--------|
| Fix memory leak in application code | Dev Team Lead | 21-June-2025 | Completed |
| Set memory alert at 80% threshold | Infrastructure Team | 15-June-2025 | Completed |
| Update application server crash runbook | Arpita Kesharwani | 18-June-2025 | Completed |
| Implement auto-restart on memory exhaustion | Dev Team Lead | 25-June-2025 | Completed |

---

## 9. Lessons Learned
- Proactive monitoring thresholds prevent P1 incidents
- Updated runbooks speed up resolution time
- Clear stakeholder communication reduces business anxiety during outages
