---
title: "[오늘의 배움] Context Switching"
excerpt: "Context Switching"

categories:
  - 오늘의배움
  - 운영체제
tags:
  - [오늘의배움, 운영체제]

toc: true
toc_sticky: true

date: 2023-01-25
last_modified_at: 2023-01-25
---

> Context Switching

하나의 프로세스가 CPU를 사용중인 상태에서 다른 프로세스가 CPU를 사용하도록 하기 위해, 먼저 사용하고 있던 프로세스의 PCB정보를
Register에 보관(저장)하고 다른 프로세스를 처리하는 과정을 말한다.

프로세스가 끝나면 Register에 저장한 먼저 사용하고 있던 프로세스의 PCB정보를 읽어 이어서 작업한다.
