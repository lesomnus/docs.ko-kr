---
title: "인스턴스 저장소 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 인스턴스 저장소
인스턴스 저장소는 인스턴스의 논리적 컨테이너입니다.이 저장소는 인스턴스 데이터와 메타데이터가 저장되는 장소입니다.인스턴스 저장소가 전용 물리적 저장소를 의미하지는 않습니다.인스턴스 저장소는 지속적인 정보를 SQL Server 데이터베이스에 포함시키거나 지속적이 아닌 정보를 메모리에 포함시킬 수 있습니다.[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]는 워크플로에서 인스턴스 데이터 및 메타데이터를 SQL Server 2005 또는 SQL Server 2008 데이터베이스에 유지할 수 있는 인스턴스 저장소의 구체적인 구현인 SQL 워크플로 인스턴스 저장소와 함께 제공됩니다.또한 Windows Server App Fabric은 인스턴스 저장소의 구체적인 구현을 제공합니다.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric 인스턴스 저장소, 쿼리 및 제어 공급자](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x412).  
  
 지속성 API는 호스트에서 인스턴스 저장소로 명령 요청\(예: <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> 및 <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>\)을 보낼 수 있는 호스트와 인스턴스 저장소 간의 인터페이스입니다.이 API의 구체적인 구현을 지속성 공급자라고 합니다.지속성 공급자는 호스트에서 요청을 받고 인스턴스 저장소를 수정합니다.  
  
 많은 인스턴스 저장소와 함께 호스트를 사용할 수 있고 많은 호스트와 함께 인스턴스 저장소를 사용할 수 있도록 호스트와 인스턴스 저장소는 플러그형입니다.인스턴스 저장소와 호스트는 독립적인 수명 주기에서 진화할 수 있지만, 일반적으로 인스턴스 저장소는 특정 호스트의 사용 패턴에 맞게 최적화됩니다.예를 들어 **WorkflowServiceHostSqlWorkflowInstanceStore**는 효과적으로 함께 작동하도록 디자인되었습니다.직접 인스턴스 저장소를 만들어 워크플로 서비스 인스턴스의 데이터와 메타데이터를 유지하고 이 인스턴스 저장소를 **WorkflowServiceHost**와 함께 사용할 수 있습니다.예를 들어 워크플로에서 SQL Server 데이터베이스에 정보를 저장하는 대신 Oracle 데이터베이스에 유지할 수 있는 OracleWorkflowInstanceStore를 만들 수 있습니다.  
  
 일반적으로 유지되는 개체를 수정하는 추가 기능을 통해 호스트가 확장됩니다.예를 들어 인스턴스 지속성 시스템에는 워크플로 호스트, "일시 중단" 작업을 지원하는 확장, SQL 인스턴스 저장소가 있을 수 있습니다.워크플로 호스트는 저장 또는 로드와 같은 표준 명령을 보내 인스턴스 저장소에서 워크플로를 저장 또는 로드하거나 워크플로를 인스턴스 저장소에 저장할 수 있습니다.일시 중단 확장은 일시 중단된 워크플로 인스턴스를 로드할 수 없도록 워크플로 인스턴스를 저장하고 로드하는 명령에 추가 의미 체계를 추가할 수 있습니다.SQL 인스턴스 저장소의 지속성 공급자는 워크플로 인스턴스를 저장하고 로드하기 위한 명령을 이해하고, SQL Server 데이터베이스에서 영구 개체 테이블을 변경하는 해당 저장 프로시저를 호출하여 명령을 구현합니다.  
  
 호스트는 인스턴스 저장소 내에서 저장소 소유자 역할을 합니다.호스트는 동시에 두 개 이상의 인스턴스 저장소가 있는 둘 이상의 인스턴스 소유자 역할을 할 수 있습니다.호스트는 인스턴스와 연결된 인스턴스 키에 GUID를 제공합니다.인스턴스 키는 인스턴스를 식별하는 고유한 별칭입니다.지속성 시스템은 호스트에서 요청한 명령을 실행할 때 인스턴스 소유자 정보를 작성, 업데이트 및 삭제합니다.  
  
 다음 목록에는 호스트와 인스턴스 저장소의 상호 작용에 관련된 중요 단계가 포함되어 있습니다.  
  
1.  지속성 공급자에서 **InstanceStore**를 가져옵니다.  
  
2.  **InstanceStore**에서 <xref:System.Runtime.Persistence.InstanceStore.CreateInstanceHandle%2A> 메서드를 호출하여 인스턴스 핸들을 가져옵니다.  
  
3.  **InstanceStore**에서 <xref:System.Runtime.Persistence.InstanceStore.Execute%2A> 메서드를 호출하여 인스턴스 핸들에 대해 명령을 호출합니다.  
  
4.  **InstanceStore.Execute**에서 반환된 <xref:System.Runtime.Persistence.InstanceView>를 검사하여 명령의 결과를 확인합니다.