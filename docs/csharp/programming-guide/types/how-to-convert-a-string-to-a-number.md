---
title: "방법: 문자열을 숫자로 변환(C# 프로그래밍 가이드) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "변환[C#]"
  - "변환[C#], string을 int로"
  - "string을 int로 변환[C#]"
  - "문자열[C#], int로 변환"
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 34
---
# 방법: 문자열을 숫자로 변환(C# 프로그래밍 가이드)
<xref:System.Convert> 클래스의 메서드를 사용하거나 다양한 숫자 형식\(int, long, float 등\)에 있는 `TryParse` 메서드를 사용하여 [문자열](../../../csharp/language-reference/keywords/string.md)을 숫자로 변환할 수 있습니다.  
  
 문자열이 있는 경우 `TryParse` 메서드\(예: `int.TryParse(“11”)`\)를 호출하면 약간 더 효율적이고 간단합니다.  `Convert` 메서드 사용은 <xref:System.IConvertible>을 구현하는 일반 개체에 더 유용합니다.  
  
 `Parse` 또는 `TryParse` 메서드는 <xref:System.Int32?displayProperty=fullName> 형식과 같이 문자열에 포함되는 숫자 형식에서 사용할 수 있습니다.  <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> 메서드는 <xref:System.Int32.Parse%2A>를 내부적으로 사용합니다.  문자열이 올바른 형식이 아닌 경우 `Parse`는 예외를 throw하는 반면 `TryParse`는 [false](../../../csharp/language-reference/keywords/false.md)를 반환합니다.  
  
## 예제  
 `Parse` 및 `TryParse` 메서드는 문자열의 시작과 끝에 있는 공백을 무시하지만 다른 모든 문자는 적절한 숫자 형식\(int, long, ulong, float, 10진수 등\)을 구성하는 문자여야 합니다.  숫자를 구성하는 문자 내에 공백이 있으면 오류가 발생합니다.  예를 들어 `decimal.TryParse`를 사용하여 “10”, “10.3”, “  10  “은 구문 분석할 수 있지만 이 메서드를 사용하여 “10X”의 10, “1 0”\(공백 확인\), “10 .3”\(공백 확인\), “10e1”\(여기서 `float.TryParse` 작동\) 등은 구문 분석할 수 없습니다.  
  
 다음 예제에서는 `Parse` 및 `TryParse`에 대한 호출이 성공하는 경우와 실패하는 경우를 모두 보여 줍니다.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_1.cs)]  
[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_2.cs)]  
[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_3.cs)]  
[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_4.cs)]  
[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_5.cs)]  
[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_6.cs)]  
  
## 예제  
 다음 표에는 사용할 수 있는 <xref:System.Convert> 클래스의 메서드 일부가 나열되어 있습니다.  
  
|숫자 형식|메서드|  
|-----------|---------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 이 예제에서는 <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> 메서드를 호출하여 입력 [string](../../../csharp/language-reference/keywords/string.md)을 [int](../../../csharp/language-reference/keywords/int.md)로 변환합니다.  코드는 이 메서드에서 throw할 수 있는 두 가지 가장 일반적인 예외인 <xref:System.FormatException>과 <xref:System.OverflowException>을 catch합니다.  정수 저장소 위치를 오버플로하지 않고 숫자를 증가시킬 수 있는 경우 프로그램에서 결과에 1을 더하여 출력을 인쇄합니다.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_1.cs)]  
[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_7.cs)]  
  
## 참고 항목  
 [형식](../../../csharp/programming-guide/types/index.md)   
 [방법: 문자열이 숫자 값을 나타내는지 확인](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)   
 [.NET Framework 4 형식 지정 유틸리티 \(영문\)](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)