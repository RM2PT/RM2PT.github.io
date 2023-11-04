---
layout: page
title: RM2PT Case Study
permalink: /casestudy/park/
typora-root-url: ../../../rm2pt-website
---

# Park System

Park System is designed for parking management. Users can pay for parking.

### System Sequence Diagrams

<img src="/imgs/cases/park-ssd.svg" alt="Alt text" style="zoom: 50%;" />

### Main Contracts of System Operations

```
Contract AutomaticEntryService::automaticEntry(plateNumber : String, time : Date) : Boolean {
    definition:
        isParking:ParkRecord = ParkRecord.allInstance()->any(r:ParkRecord|r.PlateNumber=plateNumber and r.IsParking=true)
    precondition:
        CurrentPark.oclIsUndefined() = false and
        CurrentPark.IsOpened = true and
        isParking.oclIsUndefined() = true
    postcondition:
        let parkRecord:ParkRecord in
        parkRecord.oclIsNew() and
        parkRecord.PlateNumber = plateNumber and
        parkRecord.EntryTime = time and
        parkRecord.IsParking = true and
        parkRecord.Id = self.RecordID@pre+1 and
        self.RecordID = self.RecordID@pre+1 and
        ParkRecord.allInstance()->includes(parkRecord) and
        CurrentPark.OwningRecords->includes(parkRecord) and
        result = true
}
```

### Download and Import to RM2PT

[Download RM2PT project](https://github.com/RM2PT/CaseStudies)