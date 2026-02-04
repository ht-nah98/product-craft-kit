---
name: Write Definition of Done
description: Skill viết Definition of Done (DoD) cho User Story/Sprint/Release
---

# Skill: Viết Definition of Done (DoD)

> Tuân thủ 100% template này khi viết Definition of Done

---

## Khái niệm DoD

**Definition of Done** là danh sách các tiêu chí mà một công việc PHẢI đạt được trước khi được coi là "hoàn thành".

Có 3 cấp độ DoD:

| Cấp độ | Áp dụng cho | Mục đích |
|--------|-------------|----------|
| **DoD - Story** | Mỗi User Story | Khi nào story được coi là done |
| **DoD - Sprint** | Cuối mỗi Sprint | Checklist trước khi close sprint |
| **DoD - Release** | Trước khi release | Checklist trước khi deploy production |

---

## Template: DoD cho User Story

```markdown
# Definition of Done - [US-XXX]

> Linked User Story: [US-XXX](link)

## ✅ Development Done
- [ ] Code được viết và self-tested bởi developer
- [ ] Code follow coding standards/conventions của team
- [ ] Không có TODO/FIXME còn sót trong code
- [ ] Xử lý edge cases và error handling

## ✅ Code Review Done
- [ ] Code được review bởi ít nhất 1 team member
- [ ] Tất cả comments từ review đã được address
- [ ] PR/MR được approve

## ✅ Testing Done
- [ ] Unit tests được viết và pass (coverage >= X%)
- [ ] Integration tests pass
- [ ] Manual testing hoàn thành theo AC
- [ ] Regression test pass

## ✅ Documentation Done
- [ ] Technical documentation được cập nhật (nếu cần)
- [ ] API documentation được cập nhật (nếu có API mới)
- [ ] Changelog/Release notes được ghi
- [ ] User documentation/Help được cập nhật (nếu UI thay đổi)

## ✅ Deployment Ready
- [ ] Feature được test trên staging environment
- [ ] No blockers hoặc critical bugs
- [ ] PO đã review và accept
```

---

## Template: DoD cho Sprint

```markdown
# Definition of Done - Sprint [N]

**Sprint Goal**: [Mô tả mục tiêu sprint]
**Sprint Duration**: [Start Date] - [End Date]

---

## ✅ All Stories Done
- [ ] Tất cả Story trong Sprint Backlog đã đạt DoD Story
- [ ] Không có Story nào bị carry-over (hoặc đã documented lý do)

## ✅ Quality Gates Passed
- [ ] Tổng hợp code coverage >= [X]%
- [ ] Không có Critical/High bugs mở
- [ ] Performance benchmarks đạt yêu cầu

## ✅ Integration Done
- [ ] Tất cả features đã integrate với nhau
- [ ] End-to-end testing pass
- [ ] UAT (User Acceptance Testing) hoàn thành

## ✅ Documentation Done
- [ ] Sprint report được tạo
- [ ] Burndown chart được cập nhật
- [ ] Retrospective notes được ghi

## ✅ Stakeholder Review
- [ ] Sprint Demo đã diễn ra
- [ ] Feedback từ stakeholders được ghi nhận
- [ ] PO đã sign-off
```

---

## Template: DoD cho Release

```markdown
# Definition of Done - Release [Version]

**Release Version**: [X.Y.Z]
**Target Release Date**: [Date]

---

## ✅ Feature Complete
- [ ] Tất cả features trong release scope đã done
- [ ] Feature flags được cấu hình đúng
- [ ] Backward compatibility được verify

## ✅ Quality Assurance
- [ ] Full regression test pass
- [ ] Load/Stress testing pass
- [ ] Security scan pass (no critical vulnerabilities)
- [ ] Accessibility testing pass (nếu applicable)

## ✅ Documentation Complete
- [ ] Release notes hoàn thành
- [ ] Deployment runbook cập nhật
- [ ] API documentation versioned
- [ ] User guide cập nhật

## ✅ Operational Readiness
- [ ] Monitoring/Alerting configured cho features mới
- [ ] Rollback plan documented và tested
- [ ] Support team đã được training

## ✅ Approvals
- [ ] QA Lead sign-off
- [ ] Tech Lead sign-off
- [ ] PO/PM sign-off
- [ ] [Thêm nếu cần: Security, Compliance, etc.]
```

---

## Best Practices khi viết DoD

### 1. SMART Checklist Items
```
❌ Tránh: "Code tốt"
✅ Nên: "Code có test coverage >= 80%"

❌ Tránh: "Đã test"
✅ Nên: "Manual testing hoàn thành theo tất cả AC"
```

### 2. Team Agreement
- DoD phải được cả team đồng thuận
- Review và update DoD mỗi vài sprints
- Visible cho toàn bộ team (doc hoặc board)

### 3. Not Negotiable
- DoD là tiêu chuẩn tối thiểu
- Không được skip items trong DoD
- Nếu không đạt DoD → Story chưa Done

---

## Checklist trước khi hoàn thành

- [ ] DoD rõ ràng, đo lường được
- [ ] Phù hợp với cấp độ (Story/Sprint/Release)
- [ ] Đội ngũ đã đồng thuận
- [ ] Có đủ các category: Dev, Review, Test, Doc, Deploy
