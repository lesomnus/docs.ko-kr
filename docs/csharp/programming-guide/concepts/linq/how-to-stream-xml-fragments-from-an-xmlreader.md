---
title: "방법: XmlReader에서 XML 조각 스트리밍(C#) | Microsoft 문서"
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
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
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
ms.openlocfilehash: 4bb11e120a123b701e45916b983032797c0ea8b6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>방법: XmlReader에서 XML 조각 스트리밍(C#)
큰 XML 파일을 처리해야 하는 경우 전체 XML 트리를 메모리에 로드하는 것이 가능하지 않을 수 있습니다. 이 항목에서는 <xref:System.Xml.XmlReader>를 사용하여 조각을 스트림하는 방법을 보여 줍니다.  
  
 <xref:System.Xml.XmlReader>를 사용하여 <xref:System.Xml.Linq.XElement> 개체를 읽는 가장 효과적인 방법 중 하나는 사용자 지정 축 메서드를 직접 작성하는 것입니다. 일반적으로 축 메서드는 이 항목의 예제에 나와 있는 대로 <xref:System.Xml.Linq.XElement>의 <xref:System.Collections.Generic.IEnumerable%601>과 같은 컬렉션을 반환합니다. 사용자 지정 축 메서드에서는 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 메서드를 호출하여 XML 조각을 만든 후 `yield return`을 사용하여 컬렉션을 반환합니다. 이것은 사용자 지정 축 메서드에 지연된 실행 의미를 제공합니다.  
  
 <xref:System.Xml.XmlReader> 개체에서 XML 트리를 만드는 경우 <xref:System.Xml.XmlReader>가 요소에 배치되어야 합니다. <xref:System.Xml.Linq.XNode.ReadFrom%2A> 메서드는 요소의 닫는 태그를 읽을 때까지 반환되지 않습니다.  
  
 부분 트리를 만들려는 경우 <xref:System.Xml.XmlReader>를 인스턴스화하고 <xref:System.Xml.Linq.XElement> 트리로 변환할 노드에 판독기를 배치한 다음 <xref:System.Xml.Linq.XElement> 개체를 만들 수 있습니다.  
  
 [방법: 헤더 정보에 액세스하여 XML 조각 스트리밍(C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) 항목에는 더 복잡한 문서를 스트림하는 방법에 대한 정보와 예제가 포함되어 있습니다.  
  
 [방법: 큰 XML 문서의 변환 스트리밍 수행(C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) 항목에는 LINQ to XML을 사용하여 작은 메모리 사용 공간을 유지하면서 매우 큰 XML 문서를 변환하는 예제가 포함되어 있습니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 사용자 지정 축 메서드를 만듭니다. [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 쿼리를 사용하여 이 메서드를 쿼리할 수 있습니다. 사용자 지정 축 메서드 `StreamRootChildDoc`는 반복되는 `Child` 요소가 있는 문서를 읽도록 특정하게 디자인된 메서드입니다.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 이 예제는 다음과 같은 출력을 생성합니다.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 이 예제의 소스 문서는 매우 작습니다. `Child` 요소가 수백만 있더라도 이 예제에서는 여전히 작은 메모리 공간만 사용할 것입니다.  
  
## <a name="see-also"></a>참고 항목  
 [XML 구문 분석(C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)