---
title: "끝점: Security Calls Not Authorized Per Second | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# 끝점: Security Calls Not Authorized Per Second
카운터 이름: Security Calls Not Authorized Per Second  
  
## 설명  
 올바른 사용자로부터 전송되고 적절하게 보호되지만 해당 사용자에게 특정 작업을 수행할 수 있는 권한이 없는 경우에 1초당 들어오는 메시지 수입니다.  
  
 이 카운터는 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 메서드가 `false`를 반환할 때 증가합니다.  
  
 이 카운터는 성능 카운터 형식 [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649)\(영문\)로 되어 있습니다. 이 형식의 값은 다음과 같은 수식으로 계산됩니다.  
  
 \(N 1 \- N 0 \) \/ \( \(D 1 \-D 0 \) \/ F\)