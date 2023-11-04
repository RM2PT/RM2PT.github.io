---
layout: page
title: RM2PT Case Study
permalink: /casestudy/airms/
typora-root-url: ../../../rm2pt-website
---

# Airport Management System - AirMS

AirMS is a system for airport maintenance. A ground staff can raise a work order when he finds anything abnormal. After approval, it will be assigned to maintenance workers.

### Use Case Diagram

<img src="/imgs/cases/air-ucd.png" alt="Alt text" style="zoom: 50%;" />

### Conceptual Class Diagram

<img src="/imgs/cases/air-ccd.png" alt="Alt text" style="zoom: 50%;" />

### Main Contracts of System Operations

```
Contract RepairService::approve(sid : Integer, rid : Integer, reject : Boolean, suggestion : String) : ApprovalHistory {

    definition:
        rep:Repair = Repair.allInstance()->any(u:Repair | u.Id = rid),
        sta:Staff = Staff.allInstance()->any(uu:Staff | uu.Id = sid)

    precondition:
        rep.oclIsUndefined() = false and
        sta.oclIsUndefined() = false

    postcondition:
        let ah:ApprovalHistory in
        ah.oclIsNew() and
        ah.Reject = reject and
        ah.Suggestion = suggestion and
        ApprovalHistory.allInstance()->includes(ah) and
        rep.History->includes(ah) and
        if
            reject <> false
        then
            if
                rep.Process = 0 and // STAFFREQUEST
                sta.Role = 1 // MASTER
            then
                rep.Process = 1 // MASTERAPPROVE
            else
                if
                    rep.Process = 1 and // MASTERAPPROVE
                    sta.Role = 2 // MANAGER
                then
                    rep.Process = 2 // MANAGERAPPROVE
                else
                    if
                        rep.Process = 2 and // MANAGERAPPROVE
                        sta.Role = 3 // WORKER
                    then
                        rep.Process = 3 // WORKERAPPROVE
                    endif
                endif
            endif
        else
            rep.Process = 5 // REJECT
        endif and
        Repair.allInstance()->includes(rep) and
        result = ah
}
```

### AirMS Download and Import to RM2PT

[Download RM2PT project - AirMS](https://github.com/RM2PT/CaseStudies)