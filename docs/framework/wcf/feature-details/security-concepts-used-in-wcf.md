---
title: "WCF에서 사용되는 보안 개념 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# WCF에서 사용되는 보안 개념
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 보안은 이미 사용 중인 개념을 기반으로 빌드되고 다양한 보안 인프라에 배포됩니다.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]는 HTTPS\(HTTP를 통한 SSL\(Secure Sockets Layer\)\)와 같은 이러한 인프라 중 일부를 지원합니다.그러나 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]는 SOAP 인코딩된 메시지를 통해 WS\-Security와 같은 최신 상호 운용 가능한 보안 표준을 구현하여 기존 보안 인프라를 지원하는 것 이상의 기능을 합니다.기존 메커니즘 또는 새로운 상호 운용 가능한 표준을 사용하는지 여부에 따라 두 가지의 보안 개념은 동일합니다.따라서 기존 인프라 및 최신 표준에 적용된 개념을 이해하는 것이 특정 응용 프로그램에 대해 가장 적합한 보안 모델을 구현하는 데 매우 중요합니다.  
  
## WCF 웹 서비스 보안에 대한 소개  
 Microsoft Patterns and Practices 그룹에서는 [WCF 보안 가이드](http://go.microsoft.com/fwlink/?LinkId=210210)에서 다운로드할 수 있는 WCF 보안 지침에 대한 자세한 백서를 작성했습니다.이 백서에서는 웹 서비스와 관련된 기본 보안 개념, 주요 WCF 보안 개념, 인트라넷 응용 프로그램 시나리오 및 인터넷 응용 프로그램 시나리오에 대해 설명합니다.  
  
## 산업 전반 보안 사양  
  
### 공개 키 인프라  
 PKI\(공개 키 인프라\)는 공개 키 암호화 사용을 통해 전자 트랜잭션에 참여하는 각각의 상대방을 확인하고 인증하는 디지털 인증서, 인증 기관 및 기타 등록 기관의 시스템입니다.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Server 2008 R2 인증서 서비스](http://go.microsoft.com/fwlink/?LinkId=210211)  
  
### Kerberos 프로토콜  
 *Kerberos 프로토콜*은 Windows 도메인에서 사용자를 인증하는 보안 메커니즘을 만들기 위한 사양입니다.이를 통해 사용자가 도메인 내의 다른 엔터티로 보안 컨텍스트를 설정할 수 있습니다.Windows 2000 이상 플랫폼은 기본적으로 Kerberos 프로토콜을 사용합니다.인트라넷 클라이언트와 상호 작용할 서비스를 만들 때 시스템의 메커니즘을 이해하는 것이 좋습니다.또한 *웹 서비스 보안 Kerberos 바인딩*이 널리 게시되기 때문에 Kerberos 프로토콜을 사용하여 인터넷 클라이언트와 통신할 수 있습니다. 즉, Kerberos 프로토콜의 상호 운용이 가능해집니다.Windows에서 Kerberos 프로토콜이 구현되는 방법에 대한 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]는 [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)\(영문 페이지일 수 있음\)를 참조하십시오.  
  
### X.509 인증서  
 X.509 인증서는 보안 응용 프로그램에 사용되는 기본 자격 증명 양식입니다.X.509 인증서에 대한 자세한 내용은 [X.509 공개 키 인증서](http://go.microsoft.com/fwlink/?LinkId=210213)를 참조하십시오.X.509 인증서는 인증서 저장소 내에 저장됩니다.Windows를 실행하는 컴퓨터에는 여러 종류의 인증서 저장소가 있으며 저장소마다 용도가 다릅니다.여러 저장소에 대한 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]는 [인증서 저장소](http://go.microsoft.com/fwlink/?LinkID=87787)\(영문 페이지일 수 있음\)를 참조하십시오.  
  
## 웹 서비스 보안 사양  
 시스템 정의 바인딩에서는 일반적으로 많이 사용되는 웹 서비스 보안 사양을 지원합니다.시스템 제공 바인딩 및 이 바인딩에서 지원하는 웹 서비스 사양의 전체 목록은 [시스템 제공 상호 운용성 바인딩에서 지원하는 웹 서비스 프로토콜](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)을 참조하십시오.  
  
## 액세스 제어 메커니즘  
 WCF에서는 서비스 또는 작업에 대한 액세스를 제어하는 여러 방법을 제공합니다.다음과 같은 방법이 포함됩니다.  
  
1.  <xref:System.Security.Permissions.PrinciplePermissionAttribute>  
  
2.  ASP.NET 멤버 자격 공급자  
  
3.  ASP.NET 역할 공급자  
  
4.  권한 부여 관리자  
  
5.  ID 모델  
  
 이러한 항목에 대한 자세한 내용은 [액세스 제어 메커니즘](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)을 참조하십시오.  
  
## 참고 항목  
 [보안 개요](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Windows Server App Fabric 보안 모델](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x412)