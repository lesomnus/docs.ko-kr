---
title: "XSLT 변환 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# XSLT 변환
XSLT\(Extensible Stylesheet Language Transformation\)를 사용하면 소스 XML 문서의 내용을 형식이나 구조가 다른 문서로 변환할 수 있습니다.  예를 들어, XSLT를 사용하여 XML을 웹 사이트에서 사용할 HTML로 변환하거나 응용 프로그램에서 필요한 필드만 포함하는 문서로 변환할 수 있습니다.  이 변환 프로세스는 [W3C XSLT\(XSL 변환\) 버전 1.0 권장 사항](http://go.microsoft.com/fwlink/?LinkID=49919)에 의해 지정됩니다.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 .NET Framework의 XSLT 프로세서입니다.  <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 W3C XSLT 1.0 권장 사항을 지원합니다.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> 클래스는 .NET Framework 버전 2.0에서 사용되지 않습니다.  <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 XSLT 엔진의 새로운 구현으로서,  성능 향상은 물론 새로운 보안 기능까지 제공합니다.  XSLT 응용 프로그램은 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 만드는 것이 좋습니다.  
  
## 단원 내용  
 [XslCompiledTransform 클래스 사용](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)  
 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스 사용 방법에 대한 정보를 제공합니다.  
  
 [XslTransform 클래스에서 마이그레이션](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <xref:System.Xml.Xsl.XslTransform> 클래스에서 코드를 마이그레이션하는 방법을 설명합니다.  
  
 [XSLT 컴파일러\(xsltc.exe\)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
 XSLT 컴파일러 사용 방법에 대한 정보를 제공합니다.  
  
 [XslTransform 클래스를 사용하여 XSLT 변환](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 <xref:System.Xml.Xsl.XslTransform> 클래스 사용 방법에 대한 정보를 제공합니다.  
  
 **참고** <xref:System.Xml.Xsl.XslTransform> 클래스는 .NET Framework 2.0 릴리스에서 사용되지 않습니다.  
  
## 참조  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
  
 <xref:System.Xml.Xsl.XsltArgumentList>  
  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## 관련 단원  
 [XML 문서 및 데이터](../../../../docs/standard/data/xml/index.md)