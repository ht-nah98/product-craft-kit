# Launch Checklist
## [Project Name] - [Version/Release]

---

## Document Info

| Field | Value |
|-------|-------|
| **Project** | [Project Name] |
| **Version** | [v1.0 / MVP / Beta] |
| **Target Launch** | YYYY-MM-DD |
| **Owner** | [Name] |
| **Phase** | 4. Deliver |

---

## 1. Pre-Launch Status

### 1.1 Current Status

| Area | Status | Notes |
|------|--------|-------|
| Development | 🔴 Not Started / 🟡 In Progress / 🟢 Complete | |
| Testing | 🔴 Not Started / 🟡 In Progress / 🟢 Complete | |
| Documentation | 🔴 Not Started / 🟡 In Progress / 🟢 Complete | |
| Operations | 🔴 Not Started / 🟡 In Progress / 🟢 Complete | |

### 1.2 Launch Type

| Type | Audience | Purpose | Duration |
|------|----------|---------|----------|
| ⬜ Dogfood | Internal team | Find obvious bugs | 1 week |
| ⬜ Alpha | 5-10 trusted users | Deep feedback | 1-2 weeks |
| ⬜ Beta | 50-100 users | Scale testing | 2-4 weeks |
| ⬜ GA | All users | Full release | Ongoing |

**Selected**: [Type]

---

## 2. Technical Checklist

### 2.1 Core Functionality

- [ ] All must-have features implemented
- [ ] Core user flows working end-to-end
- [ ] API endpoints functional
- [ ] Database migrations applied
- [ ] Configuration/environment variables set

### 2.2 Error Handling

- [ ] Error messages user-friendly
- [ ] Error logging in place
- [ ] Graceful degradation for failures
- [ ] Retry logic implemented (where needed)

### 2.3 Monitoring & Logging

- [ ] Application logging configured
- [ ] Metrics tracking setup
- [ ] Alerts configured for critical errors
- [ ] Dashboard created for key metrics

### 2.4 Performance

- [ ] Load testing completed
- [ ] Response times acceptable (< [X]s)
- [ ] No memory leaks identified
- [ ] Database queries optimized

### 2.5 Security

- [ ] Security review completed
- [ ] Authentication working
- [ ] Authorization/permissions correct
- [ ] Sensitive data encrypted
- [ ] No secrets in code

---

## 3. User Experience Checklist

### 3.1 Onboarding

- [ ] First-time user flow clear
- [ ] Welcome/intro screen (if applicable)
- [ ] Tutorial or tips available
- [ ] Empty states handled

### 3.2 Help & Documentation

- [ ] User guide/docs created
- [ ] FAQ prepared
- [ ] In-app help tooltips added
- [ ] Support contact info visible

### 3.3 Feedback Collection

- [ ] Feedback form/button in product
- [ ] Survey prepared for users
- [ ] Analytics tracking user actions
- [ ] Support ticket system ready

### 3.4 Known Limitations

Document known issues for users:

| Issue | Workaround | Fix ETA |
|-------|------------|---------|
| [Issue 1] | [Workaround] | [Date] |
| [Issue 2] | [Workaround] | [Date] |

---

## 4. Operations Checklist

### 4.1 Deployment

- [ ] Deployment process documented
- [ ] CI/CD pipeline working
- [ ] Staging tested
- [ ] Production deploy tested

### 4.2 Rollback Plan

**If things go wrong:**

1. [Step 1 - e.g., Revert deployment]
2. [Step 2 - e.g., Restore database]
3. [Step 3 - e.g., Notify users]

**Rollback decision criteria:**
- [Criteria 1 - e.g., >5% error rate]
- [Criteria 2 - e.g., Core flow broken]

### 4.3 Support Readiness

- [ ] Support team briefed
- [ ] Escalation path defined
- [ ] On-call rotation set (if needed)
- [ ] Runbook for common issues created

---

## 5. Metrics Tracking

### 5.1 Success Metrics (from Problem Canvas)

| Metric | Baseline | Target | Tracking Method |
|--------|----------|--------|-----------------|
| [Primary Metric] | [Value] | [Value] | [How] |
| [Secondary 1] | [Value] | [Value] | [How] |
| [Secondary 2] | [Value] | [Value] | [How] |

### 5.2 Launch Metrics

| Metric | Day 1 | Week 1 | Month 1 |
|--------|-------|--------|---------|
| New users | | | |
| Active users | | | |
| Errors | | | |
| User feedback | | | |

---

## 6. Communication Plan

### 6.1 Internal

| Audience | Message | Channel | When |
|----------|---------|---------|------|
| Team | Launch announcement | Slack | Launch day |
| Stakeholders | Status update | Email | Launch day |
| Support | Training/briefing | Meeting | Pre-launch |

### 6.2 External (if applicable)

| Audience | Message | Channel | When |
|----------|---------|---------|------|
| Beta users | Invite to try | Email | Launch day |
| All users | Feature announcement | [Channel] | GA |

---

## 7. Post-Launch Plan

### 7.1 Monitoring Period

- **Duration**: [X] days intensive monitoring
- **On-call**: [Name/Team]
- **Daily check-in**: [Time]

### 7.2 Feedback Collection

- Day 1-3: Watch for critical issues
- Week 1: Collect initial feedback
- Week 2: User interviews (5-10 users)
- Week 4: Review metrics vs targets

---

## 8. Final Go/No-Go

### 8.1 Checklist Summary

| Category | Items Complete | Ready? |
|----------|----------------|--------|
| Technical | [X]/[Y] | ⬜ Yes ⬜ No |
| User Experience | [X]/[Y] | ⬜ Yes ⬜ No |
| Operations | [X]/[Y] | ⬜ Yes ⬜ No |
| Metrics | [X]/[Y] | ⬜ Yes ⬜ No |

### 8.2 Decision

- [ ] **GO** - Proceed with launch
- [ ] **NO-GO** - Address blockers first

**Blockers (if No-Go):**
1. [Blocker 1]
2. [Blocker 2]

---

## Approvals

| Role | Name | Decision | Date |
|------|------|----------|------|
| Product Owner | | Go / No-Go | |
| Tech Lead | | Go / No-Go | |
| Ops/DevOps | | Go / No-Go | |

---

## Next Step

→ After launch, proceed to Phase 5: Iteration (collect learnings)
