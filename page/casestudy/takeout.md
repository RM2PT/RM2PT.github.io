---
layout: page
title: RM2PT Case Study
permalink: /casestudy/takeout/
typora-root-url: ../../../rm2pt-website
---

# Takeout System

Takeout is designed for user to order meal online.

### Use Case Diagram

<img src="/imgs/cases/takeout-ucd.jpg" alt="Alt text" style="zoom: 50%;" /> 

### System Sequence Diagrams

<img src="/imgs/cases/takeout-ssd.svg" alt="Alt text" style="zoom: 50%;" />

### Conceptual Class Diagram

<img src="/imgs/cases/takeout-ccd.jpg" alt="Alt text" style="zoom: 50%;" />

### Main Contracts of System Operations

```
Contract  ManageDiliveryCRUDService::createDilivery(id : String, name : String) : Boolean {
		definition:
			di:Dilivery = Dilivery.allInstance()->any(ite:Dilivery | ite.Id = id)
		precondition:
			di.oclIsUndefined() = true
		postcondition:
			let temp:Dilivery in
			temp.oclIsNew() and
			temp.Id = id and
			temp.Name = name and
			Dilivery.allInstance()->includes(temp) and
			CurrentDilivery = temp and
			result = true
}
```

### Download and Import to RM2PT

[Download RM2PT project](https://github.com/RM2PT/CaseStudies)