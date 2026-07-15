---
kind: logging_system
name: No logging system — bare console output only
category: logging_system
scope:
    - '**'
source_files:
    - index.html
---

This repository contains a single-file Thai-language calorie and macro tracker (index.html) with no dedicated logging infrastructure. There are no logger initializations, log-level configurations, structured-log helpers, or external logging libraries. The codebase does not use console.log anywhere; user feedback is delivered exclusively through in-app toast notifications (showToast) and DOM updates. Consequently, there is no logging framework, no log sinks, no level strategy, and no conventions for developers to follow.