---
title: "LINQ to Objects(C#) | Microsoft 문서"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 33402b552672fa79925fd1264444f39b19c02cd9
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-objects-c"></a>LINQ to Objects(C#)
"LINQ to Objects"란 용어는 [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) 또는 [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)과 같은 중간 LINQ 공급자 또는 API를 사용하지 않고 <xref:System.Collections.IEnumerable> 또는 <xref:System.Collections.Generic.IEnumerable%601> 컬렉션에 직접 LINQ 쿼리를 사용하는 것을 가리킵니다. LINQ를 사용하여 <xref:System.Collections.Generic.List%601>, <xref:System.Array> 또는 <xref:System.Collections.Generic.Dictionary%602>와 같은 모든 열거 가능한 컬렉션을 쿼리할 수 있습니다. 컬렉션은 사용자가 정의할 수도 있고 .NET Framework API에서 반환할 수도 있습니다.  
  
 기본적으로 LINQ to Objects는 새로운 컬렉션 방식을 나타냅니다. 이전에는 컬렉션에서 데이터를 검색하는 방법을 지정하는 복잡한 `foreach` 루프를 작성해야 했습니다. 그러나 LINQ 방식에서는 검색할 항목을 설명하는 선언적 코드를 작성합니다.  
  
 또한 LINQ 쿼리는 기존의 `foreach` 루프에 비해 세 가지 주요 이점을 제공합니다.  
  
1.  보다 간결하며 쉽게 읽을 수 있습니다(특히 여러 조건을 필터링하는 경우).  
  
2.  최소한의 응용 프로그램 코드로도 강력한 필터링, 순서 지정 및 그룹화 기능을 제공합니다.  
  
3.  거의 또는 전혀 수정하지 않고도 다른 데이터 소스에 이식할 수 있습니다.  
  
 일반적으로는 데이터에 대해 수행하려는 작업이 복잡할수록 기존의 반복 기술 대신 LINQ를 사용하면 더 큰 이점을 얻을 수 있습니다.  
  
 이 섹션에서는 몇 가지 예제를 통해 LINQ 방식에 대해 설명합니다. 여기서 설명하는 방식 외에도 다양한 방식을 사용할 수 있습니다.  
  
## <a name="in-this-section"></a>단원 내용  
 [LINQ 및 문자열(C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 LINQ를 사용하여 문자열 및 문자열 컬렉션을 쿼리하고 변환하는 방법을 설명합니다. 또한 이러한 원칙을 설명하는 항목의 링크도 제공합니다.  
  
 [LINQ 및 리플렉션(C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 LINQ에서 리플렉션을 사용하는 방식을 보여 주는 샘플 링크를 제공합니다.  
  
 [LINQ 및 파일 디렉터리(C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 LINQ를 사용하여 파일 시스템을 조작하는 방법을 설명합니다. 또한 이러한 개념을 설명하는 항목의 링크도 제공합니다.  
  
 [방법: LINQ를 사용하여 ArrayList 쿼리(C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 C#에서 ArrayList를 쿼리하는 방법을 보여 줍니다.  
  
 [방법: LINQ 쿼리용 사용자 지정 메서드 추가(C#)](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <xref:System.Collections.Generic.IEnumerable%601> 인터페이스에 확장 메서드를 추가하여 LINQ 쿼리에 사용할 수 있는 메서드 집합을 확장하는 방법을 설명합니다.  
  
 [LINQ(Language-Integrated Query)(C#)](../../../../csharp/programming-guide/concepts/linq/index.md)  
 LINQ 관련 설명과 쿼리를 수행하는 코드 예제를 제공하는 항목의 링크가 나와 있습니다.
