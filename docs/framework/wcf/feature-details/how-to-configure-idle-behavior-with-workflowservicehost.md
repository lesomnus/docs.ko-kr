---
title: "방법: WorkflowServiceHost를 사용하여 유휴 동작 구성 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 방법: WorkflowServiceHost를 사용하여 유휴 동작 구성
워크플로 인스턴스가 <xref:System.ServiceModel.Activities.Receive> 동작을 사용하여 메시지가 전달될 때까지 기다리는 경우와 같이 워크플로는 일부 외부 자극에 의해 다시 시작되어야 하는 책갈피를 만나면 유휴 상태가 됩니다.<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>는 서비스 인스턴스가 유휴 상태가 되는 시점과 인스턴스가 지속되거나 언로드되는 시점 사이의 기간을 지정할 수 있는 동작입니다. 이러한 기간을 설정할 수 있는 두 가지 속성이 포함되어 있습니다.<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>는 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 지속되는 때 사이의 시간을 지정합니다.<xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>는 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 언로드되는 때 사이의 시간을 지정합니다. 여기서, 언로드란 인스턴스를 인스턴스 스토어에 유지하고 메모리에서 제거하는 것을 의미합니다. 이 항목에서는 구성 파일에서 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>를 구성하는 방법에 대해 설명합니다.  
  
### WorkflowIdleBehavior를 구성하려면  
  
1.  다음 예제와 같이 \<`workflowIdle`\> 요소를 \<`serviceBehaviors`\> 요소 내의 \<`behavior`\> 요소에 추가합니다.  
  
    ```xml  
    <behaviors> <serviceBehaviors> <behavior name=""> <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/> </behavior> </serviceBehaviors> </behaviors>  
  
    ```  
  
     `timeToUnload` 특성은 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 언로드되는 때 사이의 시간을 지정합니다.`timeToPersist` 특성은 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 지속되는 때 사이의 시간을 지정합니다.`timeToUnload`의 기본값은 1분입니다.`timeToPersist`의 기본값은 <xref:System.TimeSpan.MaxValue>입니다. 유휴 인스턴스를 메모리에 유지하지만 견고성을 위해 지속시키려는 경우 `timeToPersist` \< `timeToUnload`가 되도록 값을 설정합니다. 유휴 인스턴스가 언로드되지 않도록 하려면 `timeToUnload`를 <xref:System.TimeSpan.MaxValue>로 설정합니다.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>[워크플로 서비스 호스트 확장](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)를 참조하세요.  
  
    > [!NOTE]
    >  위의 샘플에서 사용하는 구성은 단순화된 구성입니다.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [단순화된 구성](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### 코드에서 유휴 동작을 변경하려면  
  
-   다음 예제에서는 프로그래밍 방식으로 지속 및 언로드 전에 대기할 시간을 변경합니다.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## 참고 항목  
 [워크플로 서비스 호스트 확장](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)   
 [단순화된 구성](../../../../docs/framework/wcf/simplified-configuration.md)   
 [워크플로 서비스](../../../../docs/framework/wcf/feature-details/workflow-services.md)