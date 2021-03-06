---
title: "-target(C# 컴파일러 옵션) | Microsoft 문서"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: 22
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 615a0e2993dc78919008e8f9245504a486e2fb77
ms.lasthandoff: 03/13/2017

---
# <a name="target-c-compiler-options"></a>/target(C# 컴파일러 옵션)
**/target** 컴파일러 옵션은 다음 네 가지 형태 중 하나로 지정할 수 있습니다.  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] 앱에 대한 .exe 파일을 만듭니다.  
  
 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 .exe 파일을 만듭니다.  
  
 [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 코드 라이브러리를 만듭니다.  
  
 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 모듈을 만듭니다.  
  
 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Windows 프로그램을 만듭니다.  
  
 [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 중간 .winmdobj 파일을 만듭니다.  
  
 **/target:module**을 지정하지 않으면 **/target**은 .NET Framework 어셈블리 매니페스트가 출력 파일에 배치되도록 합니다. 자세한 내용은 [공용 언어 런타임의 어셈블리](https://msdn.microsoft.com/library/k3677y81) 및 [공통 특성](http://msdn.microsoft.com/library/2f48a7ec-9683-4899-a1d2-a08be8fc558b)을 참조하세요.  
  
 어셈블리 매니페스트는 컴파일의 첫 번째 .exe 출력 파일 또는 .exe 출력 파일이 없는 경우 첫 번째 DLL에 배치됩니다. 예를 들어 다음 명령줄에서 매니페스트는 `1.exe`에 배치됩니다.  
  
```  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 컴파일러는 컴파일당 하나의 어셈블리 매니페스트만 만듭니다. 컴파일의 모든 파일에 대한 정보가 어셈블리 매니페스트에 배치됩니다. **/target:module**을 사용하여 생성된 파일을 제외한 모든 출력 파일에 어셈블리 매니페스트가 포함될 수 있습니다. 명령줄에서 여러 출력 파일을 생성하는 경우 하나의 어셈블리 매니페스트만 만들 수 있으며, 명령줄에 지정된 첫 번째 출력 파일로 이동해야 합니다. 첫 번째 출력 파일이 **/target:exe**, **/target:winexe**, **/target:library** 또는 **/target:module** 중 무엇이든 관계없이 동일한 컴파일에서 생성된 다른 출력 파일은 모듈(**/target:module**)이어야 합니다.  
  
 어셈블리를 만드는 경우 <xref:System.CLSCompliantAttribute> 특성을 사용하여 코드의 전체 또는 일부를 CLS 규격으로 지정할 수 있습니다.  
  
```  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [C# 컴파일러 옵션](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 방법: 프로젝트 속성 및 구성 설정 수정](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)   
 [/subsystemversion(C# 컴파일러 옵션)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
