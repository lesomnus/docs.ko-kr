---
title: "방법: 형식 라이브러리에 참조 추가 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM interop, 형식 라이브러리 가져오기"
  - "형식 라이브러리 가져오기"
  - "interop 어셈블리, 생성"
  - "형식 라이브러리"
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 방법: 형식 라이브러리에 참조 추가
Visual Studio에서는 형식 라이브러리에 참조를 추가하면 메타데이터가 포함된 interop 어셈블리를 생성합니다.  주 interop 어셈블리를 사용할 수 있는 경우 Visual Studio는 새 interop 어셈블리를 생성하기 전에 기존 어셈블리를 사용합니다.  
  
### Visual Studio에서 형식 라이브러리에 대한 참조를 추가하려면  
  
1.  Windows Setup.exe 파일이 자동으로 설치를 수행하는 경우가 아니라면 컴퓨터에 COM DLL 또는 EXE 파일을 설치하세요.  
  
2.  **프로젝트**, **참조 추가**를 차례로 선택합니다.  
  
3.  참조 관리자에서 **COM**을 선택합니다.  
  
4.  목록에서 형식 라이브러리를 선택하거나 .tlb 파일을 찾습니다.  
  
5.  **확인**을 선택합니다.  
  
6.  솔루션 탐색기에서 방금 추가한 참조에 대한 바로 가기 메뉴를 열고 **속성**을 선택합니다.  
  
7.  **속성** 창에서 **Interop 형식 포함** 속성이 **True**로 설정되어 있는지 확인합니다.  이 경우 Visual Studio가 COM 형식에 대한 형식 정보를 실행 파일에 포함하므로 앱과 함께 주 interop 어셈블리를 배포할 필요가 없습니다.  
  
> [!NOTE]
>  메뉴 및 대화 상자 옵션은 사용 중인 Visual Studio 버전에 따라 다를 수 있습니다.  
  
### 명령줄 컴파일용으로 형식 라이브러리에 대한 참조를 추가하려면  
  
1.  [방법: 형식 라이브러리에서 Interop 어셈블리 생성](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)의 설명에 따라 interop 어셈블리를 생성합니다.  
  
2.  interop 어셈블리 이름을 포함한 [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md) 또는 [\/link](../Topic/-link%20\(Visual%20Basic\).md) 컴파일러 옵션을 사용하여 COM 형식에 대한 형식 정보를 실행 파일에 포함합니다.  
  
## 참고 항목  
 [형식 라이브러리를 어셈블리로 가져오기](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [.NET Framework에 COM 구성 요소 노출](../../../docs/framework/interop/exposing-com-components.md)   
 [연습: Microsoft Office 어셈블리의 형식 정보 포함](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [연습: 관리되는 어셈블리의 형식 포함](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md)   
 [\/link](../Topic/-link%20\(Visual%20Basic\).md)