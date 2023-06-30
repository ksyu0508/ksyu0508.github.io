---
layout: post
title: 계산이론
subtitle: Therory of Computation
categories: [TOC]
tags: [Development, 컴퓨터 과학]
published: false
---

## 1. Introduction

전문가 시스템(Expert Systems)는 특정 도메인에 대한 전문가 수준의 성능을 보여주는 지식 기반의 인공지능이다. 전문가 시스템은 지식 기반이기 때문에 추론과정을 관찰할 수 있으며, 쉽게 수정이 가능하다. 다양한 분야의 적용이 가능하며, 해석, 예측, 진단, 계획, 모니터링, 제어 등 다양한 분야에 응용이 가능하다.

전문가 시스템을 만들기 위해서는 지식 엔지니어링 과정을 요구로 한다. 전문가 시스템은 symbolic한 표현으로 풀 수도 있는 문제, 구조화되었지만 일반 지식은 요구하지 않는 문제, 전통적인 컴퓨팅 방법으로는 해결되지 않는 문제에 대해서 유효한 방법이다. 지식 기반의 시스템이기 때문에 전문가 시스템을 만들기 위해서는 프로젝트에 협력할 수 있는 실제 전문가가 존재하여야 한다.

전문가 혹은 인간으로 부터 지식을 습득하는 과정에는 다양한 어려움이 따른다. 전문가의 지식 혹은 기술은 무의식적인 영역도 가지고 있으며, 문제를 근본적으로 이해하고 해결하기 보다는 경험적으로 대처하는 경향도 존재한다. 또 전문가라 할지라도 개인 주관을 많이 포함하고 있으며, 일반적인 상황보다는 개인적인 상황에 맞는 지식을 가지고 있다.

규칙 기반의 전문가 시스템(Rule-Based Expert System)은 문제 해결 지식 혹은 과정을 if-else 문으로 처리하는 것이 기본적이다. Goal-driven 방법과 Data-driven 방법이 존재할 수 있다.

### 1-1. Goal-driven approach
<!-- 룰기반 전문가 시스템의 예제/goal-driven 방법 -->

<!-- 차 수리 과정의 and/or 그래프 -->

### 1-2. Data-driven approach

Data-driven 방벙에서는 BFS가 일반적으로 적용된다.

## 2. Overview of Expert System Technology

## 3. Rule-Based Expert Systems

## 4. Model-Based, Case-Based and Hybrid Systems

 인간 전문가의 규칙은 판단 과정에서 많은 부분을 생략하여 설명하고, 관찰 가능한 결과와 최종 결정 사이의 부분을 중간과정 없이 직관으로 직접 연관 시키는 경우가 많다. 이러한 점은 기존 전문가 시스템의 한계점으로 드러날 수 밖에 없다.

## 4-1. Model-Based System

 이를 개선하기 위한 방법중의 하나인 모델 기반의 시스템은 실제 물리적인 시스템의 명세와 기능을 직접적으로 구현한 지식 기반의 추론자라고 할 수 있다. 대표적인 예시로는 튜터링 시스템이 있는데, 동작을 관찰함으로서 어떠한 구성 요소가 문제가 발생했는지를 결정하는 것이다.

 모델 기반 시스템 방법으로는 DAVIS & Hamscher(1992)의 덧셈 계산자(adder)의 동작에 관한 것이 있다. 모델 기반 추론의 목표는 덧셈 계산자를 포착하고 이것을 지식 기반으로 표현하는 것이다.

 덧셈기와 곱셈기로 구성된 임의의 회로에 대해서 먼저
 * 가설 생성: 예상 결과와 불일치가 발생했을 경우, 장치의 어떤 구성 요소가 원인이 될 수 있는지에 대한 가설을 수립
 * 가설 검증: 관찰된 동작을 설명할 수 있는 변수들 결정
 * 가설: 다수의 가설이 남은 경우, 하나의 가설을 남길 수 있는 추가 정보를 수집할 수 있는 지 결정

두 번째 예시로는 나사의 로켓에 관한 내용이다. Williams & Nayak (1996b)은 리빙스톤 호의 추진 시스템을 모델 기반의 설정 관리 시스템을 만들었다. 시스템의 밸브의 상태 전이는 낮은 확률을 통하여 정상 작동과 비정상 상태로 나누어지게 된다. 즉 모델 기반 시스템에서 밸브를 열려고 시도하면 1%의 확률로 밸브가 열린 상태로 멈추거나, 혹은 닫힌 상태에서 작동하지 않을 수도 있다는 얘기이다. 이러한 전이 시스템 모델을 통해서 실제 시스템의 모드를 추정할 수 있도록 한 것이다.

### 4-2. Case-Based Reasoning(CBR)

사례 기반 추론은 과거의 문제 상황과 그에 따른 해법을 가지고 있는 실제 사례로 부터 추론을 진행하는 벙법이다. 이러한 CBR은 일반적으로 다음과 같은 구조를 나타낸다:

1. 메모리로부터 적합한 사례를 가져옴
2. 가져온 사례를 현재 상황에 맞게 변형
3. 변형된 사례를 적용
4. 해법을 도출

도출된 해법은 성공여부를 포함하여 다시 메모리에 저장하며, 시스템은 새로 저장된 case를 추론에서 다시 사용할 수 있다. Kolodner(1993)은 사례를 검색하고 정렬하는 데 사용할 수 있는 휴리스틱을 제시하였는데, 이러한 휴리스틱에는 현재 사례를 부분적으로 나누고 그 부분에 대해서 동일한 목표를 가지고 있는지, 현재 사례의 특징과 유사한 특징을 많이 가지고 있거나 우선순위가 높은 특징을 가지고 있는지, 일반적으로 많이 사용되는 case인지, 최근에 사용되었는지, 현재 사례에 적용하기 쉬운 사례인지 등이 제시되었다.


## 5. Planning

작업 계획이란 특정 작업을 수행하기 위한 일련의 행동들을 찾는 것이다. 
물건을 옮기는 로봇을 예시로 할 경우에, 특정 timestep에서의 상태를 predicate로 표현할 경우

실제 모델의 상태나 규칙을 재현할 수 있도록 predicate들 간의 axiom을 먼저 정의한 후에, 새로운 상태를 만들 수 있는 operator를 추가로 정의한다. 이럴 경우에 결국 작업 계획은 state space search 문제로 표현할 수 있게 되며, 시작 상태로부터 목표 상태를 찾기 위해 그래프 탐색 기법들을 활용할 수 있게 된다.


 