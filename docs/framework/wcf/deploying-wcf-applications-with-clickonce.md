---
title: "ClickOnce를 사용하여 WCF 응용 프로그램 배포 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a11feee-2a47-4d3e-a28a-ad69d5ff93e0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ClickOnce를 사용하여 WCF 응용 프로그램 배포
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]를 사용하는 클라이언트 응용 프로그램은 ClickOnce 기술을 사용하여 배포할 수 있습니다.클라이언트 응용 프로그램이 신뢰할 수 있는 인증서를 사용하여 디지털 방식으로 서명되는 경우, 이 기술을 통해 클라이언트 응용 프로그램은 코드 액세스 보안에서 제공하는 런타임 보안 보호의 이점을 활용할 수 있습니다.ClickOnce 응용 프로그램 서명에 사용되는 인증서는 신뢰할 수 있는 게시자 저장소에 있어야 하며, 클라이언트 컴퓨터의 로컬 보안 정책은 게시자의 인증서를 사용하여 서명된 응용 프로그램에 완전 신뢰 권한을 부여하도록 구성되어야 합니다.  
  
 ClickOnce 응용 프로그램 및 신뢰할 수 있는 게시자 구성에 대한 자세한 내용은 [Configuring ClickOnce Trusted Publishers](http://go.microsoft.com/fwlink/?LinkId=94774)를 참조하십시오.  
  
## 참고 항목  
 [신뢰할 수 있는 응용 프로그램 배포 개요](http://go.microsoft.com/fwlink/?LinkId=94775)   
 [Windows Forms 응용 프로그램에 대한 ClickOnce 배포](http://go.microsoft.com/fwlink/?LinkId=94776)