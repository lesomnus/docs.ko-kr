---
title: "쿼리 식 구문 예제: 요소 연산자 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 쿼리 식 구문 예제: 요소 연산자
이 항목의 예제에서는 <xref:System.Linq.Enumerable.First%2A> 메서드를 사용하여 쿼리 식 구문으로 [AdventureWorks Sales 모델](http://msdn.microsoft.com/ko-kr/f16cd988-673f-4376-b034-129ca93c7832)을 쿼리하는 방법을 보여 줍니다.  이 예제에서 사용하는 AdventureWorks Sales 모델에서는 AdventureWorks 샘플 데이터베이스의 Contact, Address, Product, SalesOrderHeader 및 SalesOrderDetail 테이블을 사용합니다.  
  
 이 항목의 예제에서는 다음과 같은 `using`\/`Imports` 문을 사용합니다.  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## First  
  
### 예제  
 다음 예제에서는 <xref:System.Linq.Enumerable.First%2A> 메서드를 사용하여 이름이 "Brooke"인 첫 번째 연락처를 반환합니다.  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## 참고 항목  
 [LINQ to Entities의 쿼리](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)