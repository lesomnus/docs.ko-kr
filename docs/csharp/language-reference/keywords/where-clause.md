---
title: "where 절(C# 참조) | Microsoft 문서"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1094f68293dd05fdfe69a39016689cbaa3fd6290
ms.lasthandoff: 03/13/2017

---
# <a name="where-clause-c-reference"></a>where 절(C# 참조)
`where` 절은 데이터 소스의 어떤 요소가 쿼리 식에서 반환될지를 지정하기 위해 쿼리 식에서 사용됩니다. 또한 각 소스 요소(범위 변수로 참조됨)에 부울 조건(*predicate*)을 적용하고 지정된 조건이 참인 요소를 반환합니다. 단일 쿼리 식에는 여러 `where` 절을 포함할 수 있으며 단일 절에는 여러 조건부 하위 식을 포함할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음 예제에서 `where` 절은 5보다 작은 숫자를 제외한 모든 숫자를 필터링합니다. `where` 절을 제거하면 데이터 소스의 모든 숫자가 반환됩니다. `num < 5` 식은 각 요소에 적용되는 조건자입니다.  
  
 [!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a>예제  
 단일 `where` 절 내에서 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 및 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 연산자를 사용하여 조건자를 필요한 만큼 지정할 수 있습니다. 다음 예제에서 쿼리는 5 미만의 짝수만 선택하도록 두 개의 조건자를 지정합니다.  
  
 [!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a>예제  
 `where` 절에는 부울 값을 반환하는 메서드를 하나 이상 포함할 수 있습니다. 다음 예제에서 `where` 절은 메서드를 사용하여 범위 변수의 현재 값이 짝수인지 홀수인지를 확인합니다.  
  
 [!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a>주의  
 `where` 절은 필터링 메커니즘입니다. 첫 번째 또는 마지막 절이 될 수 없다는 점을 제외하고, 쿼리 식의 거의 모든 곳에 배치할 수 있습니다. 소스 요소를 그룹화 전에 필터링할지, 그룹화 후에 필터링할지에 따라 `where` 절은 [group](../../../csharp/language-reference/keywords/group-clause.md) 절 앞 또는 뒤에 나타날 수 있습니다.  
  
 지정된 조건자가 데이터 소스의 요소에 대해 유효하지 않은 경우, 컴파일 시간 오류가 발생합니다. 이는 [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]에서 제공하는 강력한 형식 검사의 이점 중 하나입니다.  
  
 컴파일 시간에 `where` 키워드는 <xref:System.Linq.Enumerable.Where%2A> 표준 쿼리 연산자 메서드에 대한 호출로 변환됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [쿼리 키워드(LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [From 절](../../../csharp/language-reference/keywords/from-clause.md)   
 [Select 절](../../../csharp/language-reference/keywords/select-clause.md)   
 [데이터 필터링](http://msdn.microsoft.com/library/cee88d0f-31aa-4c60-9452-cc122ed0057d)   
 [LINQ 쿼리 식](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [C#에서 LINQ 시작](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
