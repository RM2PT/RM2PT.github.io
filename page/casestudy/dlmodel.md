---
layout: page
title: RM2PT Case Study
permalink: /casestudy/dlmodel/
typora-root-url: ../../../rm2pt-website
---

# Deep Learning Model - DLModel

DLModel is designed for deep learning models management. User can search, upload or download models.

### Use Case Diagram

<img src="/imgs/cases/dlmodel-ucd.png" alt="Alt text" style="zoom: 50%;" /> 

### System Sequence Diagrams

<img src="/imgs/cases/dlmodel-ssd.svg" alt="Alt text" style="zoom: 50%;" />

### Conceptual Class Diagram

<img src="/imgs/cases/dlmodel-ccd.png" alt="Alt text" style="zoom: 50%;" />

### Main Contracts of System Operations

```
Contract DownloadModelService::searchModelByKeyword(keyword : String) : Set(Model) {

    precondition:
        keyword <> ""
    postcondition:
        result = Model.allInstance()->select(m:Model| m.Keyword = keyword)
}

Contract DLModelMS1System::viewModel(modelId : String) : Model {

    definition:
        a:Model = Model.allInstance()->any(b:Model| b.Id = modelId)

    precondition:
        a.oclIsUndefined() = false
    postcondition:
        self.CurrentModel = a and
        result = a
}

Contract DownloadModelService::downModel(id : String): Boolean {

    definition:
        a:Model = Model.allInstance()->any(b:Model| b.Id = id)

    precondition:
        a.oclIsUndefined() = false
    postcondition:
        download(a.ModeltoAttachment.URL) and
        result = true
}

Contract ManageModelService::updateModelInformation(id : String, title : String, keyword : String, version : String, description : String) : Boolean {

    definition:
        e:Model = Model.allInstance()->any(b:Model| b.Id = id)

    precondition:
        e.oclIsUndefined() = false

    postcondition:
        e.Id = id and
        e.Title = title and
        e.Keyword = keyword and
        e.Version = version and
        e.Description = description and
        e.LastUpdateTime.isEqual(Now) and
        result = true
}
```

### Download and Import to RM2PT

[Download RM2PT project](https://github.com/RM2PT/CaseStudies)