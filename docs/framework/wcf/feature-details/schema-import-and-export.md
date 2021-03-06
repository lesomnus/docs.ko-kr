---
title: "스키마 가져오기 및 내보내기 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, 스키마 가져오기 및 내보내기"
  - "XsdDataContractExporter 클래스"
  - "XsdDataContractImporter 클래스"
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 스키마 가져오기 및 내보내기
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]새 serialization 엔진을 포함 된 <xref:System.Runtime.Serialization.DataContractSerializer>합니다. `DataContractSerializer`는 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 개체와 XML을 양방향으로 변환합니다. 이 serializer 이외에도, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에는 관련 스키마를 가져오고 내보내는 메커니즘이 있습니다. *스키마* serializer가 생성 하거나 deserializer가 액세스할 수 있는 XML의 모양, 되 고 컴퓨터가 읽을 수 있는 설명입니다. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에서는 여러 타사 플랫폼과 상호 운용할 수 있는 W3C(World Wide Web 컨소시엄) XSD(XML 스키마 정의 언어)를 스키마 표현으로 사용합니다.  
  
 스키마 가져오기 구성 요소인 <xref:System.Runtime.Serialization.XsdDataContractImporter>는 XSD 스키마 문서를 사용 하 고 생성, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (일반적으로 데이터 계약 클래스) 클래스를 serialize 된 형태가 해당 지정된 된 스키마에 일치 되도록 합니다.  
  
 예를 들어 다음과 같은 스키마 단편이 있습니다.  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 코드를 보다 쉽게 파악할 수 있도록 간소화된 다음과 같은 형식을 생성합니다.  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 생성 된 형식을 따르는지 몇 가지 데이터 계약 모범 사례를 참고 (에 [모범 사례: 데이터 계약 버전 관리](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)):  
  
-   형식에서 구현 하는 <xref:System.Runtime.Serialization.IExtensibleDataObject> 인터페이스입니다. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][이후 버전과 호환 데이터 계약](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)합니다.  
  
-   데이터 멤버는 private 필드를 래핑하는 public 속성으로 구현됩니다.  
  
-   클래스는 부분 클래스로, 생성된 코드를 수정하지 않고 추가 클래스를 만들 수 있습니다.  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> 반대로 할 수 있습니다-와 직렬화 할 수 있는 형식을 `DataContractSerializer` 및 XSD 스키마 문서를 생성 합니다.  
  
## <a name="fidelity-is-not-guaranteed"></a>정확도는 보장되지 않음  
 스키마나 형식을 통해 완벽히 정확한 라운드트립을 만든다고 보장할 수 없습니다. (A *왕복* 클래스의 집합을 만들고 스키마를 다시 만들기 위해 그 결과 내보낼 스키마를 가져오는 것을 의미 합니다.) 이 경우 동일한 스키마는 반환되지 않습니다. 이 프로세스를 반대로 해도 정확도는 보장되지 않습니다. (형식의 스키마를 생성하기 위해 형식을 내보낸 다음 그 형식을 다시 가져옵니다.) 이때도 동일한 형식은 반환되지 않을 것입니다.  
  
## <a name="supported-types"></a>지원 형식  
 데이터 계약 모델은 WC3 스키마의 제한된 하위 집합만 지원합니다. 이 하위 집합을 따르지 않는 스키마는 가져오기 프로세스 동안 예외를 발생시킵니다. 예를 들어 데이터 계약의 데이터 멤버가 XML 특성으로 serialize되도록 지정하는 방법이 없다고 가정합니다. 이 경우, XML 특성을 사용하도록 하는 스키마는 지원되지 않고, 올바른 XML 프로젝션으로 데이터 계약을 생성할 수 없으므로 가져오기 작업 동안 예외가 발생됩니다.  
  
 예를 들어 다음과 같은 스키마 단편은 가져오기 기본 설정을 사용하여 가져올 수 없습니다.  
  
 <!-- TODO: review snippet reference [!code[c_SchemaImportExport#9](../../../../samples/snippets/common/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  -->  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][데이터 계약 스키마 참조](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)합니다. 스키마가 데이터 계약 규칙을 따르지 않으면 다른 serialization 엔진을 사용합니다. 예를 들어는 <xref:System.Xml.Serialization.XmlSerializer> 자체 별도 스키마 가져오기 메커니즘을 사용 합니다. 또한 지원되는 스키마 범위가 확장되는 특별한 가져오기 모드도 있습니다. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]생성 하는 방법에 대 한 섹션 <xref:System.Xml.Serialization.IXmlSerializable> 의 형식은 [스키마를 생성 하는 클래스를 가져와서](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)합니다.  
  
 `XsdDataContractExporter`는 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]로 serialize할 수 있는 모든 `DataContractSerializer` 형식을 지원합니다. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][데이터 계약 Serializer에서 지 원하는 형식](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)합니다. 스키마를 사용 하 여 생성는 `XsdDataContractExporter` 정상적으로 사용할 수 있는 데이터는 하는 `XsdDataContractImporter` 사용할 수 (하지 않는 한는 <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> 스키마를 사용자 지정 하는 데 사용 됩니다).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]사용 하는 <xref:System.Runtime.Serialization.XsdDataContractImporter>, 참조 [스키마를 생성 하는 클래스를 가져와서](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)합니다.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]사용 하는 <xref:System.Runtime.Serialization.XsdDataContractExporter>, 참조 [클래스에서 스키마 내보내기](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Runtime.Serialization.XsdDataContractImporter>   
 <xref:System.Runtime.Serialization.XsdDataContractExporter>   
 [스키마를 가져와 클래스 생성](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)   
 [클래스에서 스키마 내보내기](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)