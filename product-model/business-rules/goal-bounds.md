---
appliesTo:
- type: entity
  id: goals
references:
- kind: code
  role: implementation
  target: src/pipeline/goals.ts#GOAL_LIMITS
- kind: code
  role: implementation
  target: src/pipeline/derive.ts#estimatedSleepTarget
---

# Personal goals stay within supported bounds and increments

Steps range from 2000 to 25000 by 500; brisk minutes from 10 to 120 by five; explicit sleep need from 420 to 540 minutes by 15. Auto sleep need is the median night held within 420–510 minutes, or 450 without recorded nights. The weekly 150-minute guideline counts vigorous minutes twice and is not a personal setting.
