---
title: "인증서 클라이언트를 사용하는 메시지 보안 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# 인증서 클라이언트를 사용하는 메시지 보안
다음 시나리오에서는 메시지 보안 모드를 사용하여 보호되는 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 클라이언트 및 서비스를 보여 줍니다.클라이언트 및 서비스는 인증서를 사용하여 인증됩니다.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][분산 응용 프로그램 보안](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).  
  
 샘플 응용 프로그램을 보려면 [메시지 보안 인증서](../../../../docs/framework/wcf/samples/message-security-certificate.md)를 참조하십시오.  
  
 ![인증서가 있는 클라이언트](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")  
  
|특성|설명|  
|--------|--------|  
|보안 모드|메시지|  
|상호 운용성|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]에만 해당|  
|인증\(서버\)|서비스 인증서 사용|  
|인증\(클라이언트\)|클라이언트 인증서 사용|  
|무결성|예|  
|기밀성|예|  
|전송|HTTP|  
|바인딩|<xref:System.ServiceModel.WSHttpBinding>|  
  
## 서비스  
 다음 코드와 구성은 독립적으로 실행되어야 합니다.다음 작업 중 하나를 수행합니다.  
  
-   구성 없이 코드를 사용하여 독립 실행형 서비스를 만듭니다.  
  
-   제공된 구성을 사용하여 서비스를 만들지만 끝점을 정의하지 않습니다.  
  
### 코드  
 다음 코드에서는 안전한 컨텍스트를 설정하기 위해 메시지 보안을 사용하는 서비스 끝점을 만드는 방법을 보여 줍니다.  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### 구성  
 코드 대신 다음 구성을 사용할 수 있습니다.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCerficiateClient"   
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## 클라이언트  
 다음 코드와 구성은 독립적으로 실행되어야 합니다.다음 작업 중 하나를 수행합니다.  
  
-   이 코드와 클라이언트 코드를 사용하여 독립 실행형 클라이언트를 만듭니다.  
  
-   끝점 주소를 정의하지 않는 클라이언트를 만듭니다.대신 구성 이름을 인수로 사용하는 클라이언트 생성자를 사용합니다.예를 들면 다음과 같습니다.  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### 코드  
 다음 코드에서는 클라이언트를 만듭니다.바인딩은 메시지 모드 보안으로 설정되며 클라이언트 자격 증명 형식은 `Certificate`로 설정됩니다.  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### 구성  
 다음 구성에서는 끝점 동작을 사용하는 클라이언트 인증서를 지정합니다.인증서에 대한 자세한 내용은 [인증서 작업](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)을 참조하십시오.또한 코드에서도 \<`identity`\> 요소를 사용하여 예상 서버 ID의 DNS\(Domain Name System\)를 지정합니다.ID에 대한 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]는 [서비스 ID 및 인증](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)을 참조하십시오.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 참고 항목  
 [보안 개요](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [서비스 ID 및 인증](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [인증서 작업](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Windows Server App Fabric 보안 모델](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x412)