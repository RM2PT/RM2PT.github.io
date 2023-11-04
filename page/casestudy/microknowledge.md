---
layout: page
title: RM2PT Case Study
permalink: /casestudy/microknowledge/
typora-root-url: ../../../rm2pt-website
---

# Micro-Knowledge

Micro-Knowledge is designed for share ideas. Users can share their ideas and comment on others' ideas like posting.

### System Sequence Diagrams

<img src="/imgs/cases/microknowledge-ssd.svg" alt="Alt text" style="zoom: 50%;" />

### Conceptual Class Diagram

<img src="/imgs/cases/microknowledge-ccd.png" alt="Alt text" style="zoom: 50%;" />

### Main Contracts of System Operations

```
Contract MicroKnowledgeSystem::writeComment(content:String) : Boolean {
    precondition:
        CurrentMicroknowledge.oclIsUndefined() = false and
        CurrentUser.oclIsUndefined() = false
    postcondition:
        let comment:Comment in
        comment.oclIsNew() and
        comment.Content = content and
        comment.WritingTime.isEqual(Now) and
        Comment.allInstance()->includes(comment) and
        CurrentMicroknowledge.ContainedComment->includes(comment) and
        comment.CommenttoMicroknowledge = CurrentMicroknowledge and
        CurrentUser.ReadertoComment->includes(comment) and
        comment.CommenttoReader = CurrentUser and
        result = true
}
```

### Download and Import to RM2PT

[Download RM2PT project](https://github.com/RM2PT/CaseStudies)