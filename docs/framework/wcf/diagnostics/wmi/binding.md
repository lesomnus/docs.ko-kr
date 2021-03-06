---
title: "바인딩 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 바인딩
wmi 바인딩  
  
## 구문  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## 메서드  
 Binding 클래스는 메서드를 정의하지 않습니다.  
  
## 속성  
 Binding 클래스에는 다음과 같은 속성이 있습니다.  
  
### BindingElements  
 데이터 형식: BindingElement array  
  
 액세스 형식: 읽기 전용  
  
 바인딩이 구현한 바인딩 요소의 컬렉션입니다.  
  
### CloseTimeout  
 데이터 형식: datetime  
  
 액세스 형식: 읽기 전용  
  
 닫기 작업을 완료하기 위해 제공된 시간 간격입니다.  
  
### Name  
 데이터 형식: string  
  
 액세스 형식: 읽기 전용  
  
 바인딩 이름입니다.  
  
### 네임스페이스  
 데이터 형식: string  
  
 액세스 형식: 읽기 전용  
  
 바인딩의 XML 네임스페이스입니다.  
  
### OpenTimeout  
 데이터 형식: datetime  
  
 액세스 형식: 읽기 전용  
  
 열기 작업을 완료하기 위해 제공된 시간 간격입니다.  
  
### ReceiveTimeout  
 데이터 형식: datetime  
  
 액세스 형식: 읽기 전용  
  
 받기 작업을 완료하기 위해 제공된 시간 간격입니다.  
  
### Scheme  
 데이터 형식: string  
  
 액세스 형식: 읽기 전용  
  
 바인딩이 빌드한 채널 및 수신기 팩터리에서 사용하는 URI 전송 체계입니다.  
  
### SendTimeout  
 데이터 형식: datetime  
  
 액세스 형식: 읽기 전용  
  
 보내기 작업을 완료하기 위해 제공된 시간 간격입니다.  
  
## 요구 사항  
  
|MOF|Servicemodel.mof에 선언되어 있습니다.|  
|---------|----------------------------------|  
|네임스페이스|root\\ServiceModel에 정의되어 있습니다.|  
  
## 참고 항목  
 <xref:System.ServiceModel.Channels.Binding>