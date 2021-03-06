---
title: "Implementing the UI Automation Scroll Control Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI Automation, Scroll control pattern"
  - "control patterns, Scroll"
  - "Scroll control pattern"
ms.assetid: 73d64242-6cbb-424c-92dd-dc69530b7899
caps.latest.revision: 23
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 23
---
# Implementing the UI Automation Scroll Control Pattern
> [!NOTE]
>  이 설명서는 <xref:System.Windows.Automation> 네임스페이스에 정의된 관리되는 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 클래스를 사용하려는 .NET Framework 개발자를 위한 것입니다.[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]에 대한 최신 정보는 [Windows 자동화 API: UI 자동화](http://go.microsoft.com/fwlink/?LinkID=156746)를 참조하세요.  
  
 이 항목에서는 이벤트 및 속성에 대한 정보를 포함하여 <xref:System.Windows.Automation.Provider.IScrollProvider>를 구현하기 위한 지침 및 규칙을 제공합니다. 추가 참조에 대한 링크는 항목 끝에 나열되어 있습니다.  
  
 <xref:System.Windows.Automation.ScrollPattern> 컨트롤 패턴은 자식 개체의 컬렉션에 대해 스크롤할 수 있는 컨테이너 역할을 하는 컨트롤을 지원하는 데 사용됩니다. 이 컨트롤은 스크롤 기능을 지원하기 위해 스크롤 막대를 사용할 필요는 없지만 일반적으로는 스크롤 막대를 사용합니다.  
  
 ![스크롤 막대 없는 Scroll 컨트롤](../../../docs/framework/ui-automation/media/uia-scrollpattern-without-scrollbars.PNG "UIA\_ScrollPattern\_Without\_Scrollbars")  
스크롤 막대를 사용하지 않는 스크롤 컨트롤의 예제  
  
 이 컨트롤을 구현하는 컨트롤의 예제를 보려면 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)을 참조하세요.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## 구현 지침 및 규칙  
 Scroll 컨트롤 패턴을 구현할 때는 다음 지침 및 규칙에 유의하세요.  
  
-   이 컨트롤의 자식 항목은 <xref:System.Windows.Automation.Provider.IScrollItemProvider>를 구현해야 합니다.  
  
-   컨테이너 컨트롤의 스크롤 막대는 <xref:System.Windows.Automation.ScrollPattern> 컨트롤 패턴을 지원하지 않습니다. 이 스크롤 막대는 <xref:System.Windows.Automation.RangeValuePattern> 컨트롤 패턴을 지원해야 합니다.  
  
-   스크롤이 백분율로 측정되면, 스크롤 눈금과 관련된 모든 값 또는 양은 0에서 100까지의 범위로 정규화되어야 합니다.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> 및 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>는 <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>와 관계가 없습니다.  
  
-   <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> \= `false`일 경우 <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>는 100%로 설정되어야 하며 <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>는 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>로 설정되어야 합니다. 마찬가지로, <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> \= `false`일 경우 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>는 100%로 설정되어야 하며 <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>는 <xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>로 설정되어야 합니다. 따라서 클라이언트가 원하지 않는 스크롤 방향이 활성화되어 있는 경우 UI 자동화 클라이언트는 [경합 상태](http://support.microsoft.com/default.aspx?scid=kb;en-us;317723)를 방지하면서 <xref:System.Windows.Automation.ScrollPattern.SetScrollPercent%2A> 메서드 내에서 이러한 속성 값을 사용할 수 있습니다.  
  
-   <xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>는 로캘과 관련됩니다. HorizontalScrollPercent \= 100.0으로 설정하는 경우 왼쪽에서 오른쪽으로 읽는 언어\(예: 영어\)에서 컨트롤의 스크롤 위치는 맨 오른쪽 위치에 해당하는 값으로 설정해야 합니다. 또는 오른쪽에서 왼쪽으로 읽는 언어\(예: 아랍어\)의 경우 HorizontalScrollPercent \= 100.0으로 설정할 경우 스크롤 위치는 맨 왼쪽 위치로 설정해야 합니다.  
  
<a name="Required_Members_for_IScrollProvider"></a>   
## IScrollProvider에 필요한 멤버  
 <xref:System.Windows.Automation.Provider.IScrollProvider>를 구현하려면 다음과 같은 속성 및 메서드가 필요합니다.  
  
|필요한 멤버|멤버 형식|노트|  
|------------|-----------|--------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalScrollPercent%2A>|속성|없음|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalScrollPercent%2A>|속성|없음|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontalViewSize%2A>|속성|없음|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticalViewSize%2A>|속성|없음|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.HorizontallyScrollable%2A>|속성|없음|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.VerticallyScrollable%2A>|속성|없음|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>|메서드|없음|  
|<xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>|메서드|없음|  
  
 이 컨트롤 패턴에 연결된 이벤트가 없습니다.  
  
<a name="Exceptions"></a>   
## 예외  
 공급자는 다음과 같은 예외를 throw해야 합니다.  
  
|예외 형식|조건|  
|-----------|--------|  
|<xref:System.ArgumentException>|컨트롤이 가로 또는 세로 스크롤에 대해서만 <xref:System.Windows.Automation.ScrollAmount> 값을 지원하지만 <xref:System.Windows.Automation.ScrollAmount> 값이 전달되는 경우에 <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A>은 이 예외를 발생시킵니다.|  
|<xref:System.ArgumentException>|double로 변환할 수 없는 값이 전달되는 경우 <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>가 이 예외를 발생시킵니다.|  
|<xref:System.ArgumentOutOfRangeException>|100보다 크거나 0보다 작은 값이 전달되는 경우\(<xref:System.Windows.Automation.ScrollPatternIdentifiers.NoScroll>에 해당하는 \-1 제외\) <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A>가 이 예외를 발생시킵니다.|  
|<xref:System.InvalidOperationException>|지원되지 않는 방향으로 스크롤이 시도되면 <xref:System.Windows.Automation.Provider.IScrollProvider.Scroll%2A> 및 <xref:System.Windows.Automation.Provider.IScrollProvider.SetScrollPercent%2A> 둘 다 이 예외를 발생시킵니다.|  
  
## 참고 항목  
 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)   
 [Support Control Patterns in a UI Automation Provider](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)   
 [UI Automation Control Patterns for Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)   
 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)