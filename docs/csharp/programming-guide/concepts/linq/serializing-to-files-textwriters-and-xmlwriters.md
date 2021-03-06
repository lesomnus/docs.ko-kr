---
title: "Files, TextWriters 및 XmlWriters로 serialize1 | Microsoft 문서"
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
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
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
ms.openlocfilehash: f61324395e81509e5800e99b654a8c669d4397f0
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Files, TextWriters 및 XmlWriters로 serialization
XML 트리를 <xref:System.IO.File>, <xref:System.IO.TextWriter> 또는 <xref:System.Xml.XmlWriter>로 serialize할 수 있습니다.  
  
 `ToString` 메서드를 사용하여 <xref:System.Xml.Linq.XDocument> 및 <xref:System.Xml.Linq.XElement>와 같은 XML 구성 요소를 문자열로 serialize할 수 있습니다.  
  
 문자열로 serialize할 때 서식 지정을 방지하려면 <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> 메서드를 사용하면 됩니다.  
  
 파일로 serialize할 때의 기본 동작은 생성되는 XML 문서의 서식을 지정하는(들여쓰는) 것입니다. 들여쓰는 경우 XML 트리의 무효 공백은 유지되지 않습니다. 서식을 사용하여 serialize하려면 <xref:System.Xml.Linq.SaveOptions>를 인수로 사용하지 않는 다음 메서드의 오버로드 중 하나를 사용합니다.  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 들여쓰지 않고 XML 트리에서 무효 공백을 유지하려면 <xref:System.Xml.Linq.SaveOptions>를 인수로 사용하는 다음 메서드의 오버로드 중 하나를 사용합니다.  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 예제를 보려면 적절한 참조 항목을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [XML 트리 serialize(C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
