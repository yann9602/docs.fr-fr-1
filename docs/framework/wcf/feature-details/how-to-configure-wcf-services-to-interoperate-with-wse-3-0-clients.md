---
title: "Comment : configurer les services WCF pour interagir avec les clients WSE 3.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5589ad8e4193416738da98676551bbf82c128a79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>Comment : configurer les services WCF pour interagir avec les clients WSE 3.0
Les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont compatibles au niveau câble avec les services Web Services Enhancements 3.0 for Microsoft .NET (WSE) lorsque les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont configurés pour utiliser la version d'août 2004 de la spécification WS-Addressing.  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>Pour permettre à un service WCF d'interagir avec les clients WSE 3.0  
  
1.  Définissez une liaison personnalisée pour le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
     Pour indiquer que la version d’août 2004 de la spécification WS-Addressing est utilisée pour l’encodage des messages, il est nécessaire de créer une liaison personnalisée.  
  
    1.  Ajouter un enfant [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) à la [ \<liaisons >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration du service.  
  
    2.  Spécifiez un nom pour la liaison, en ajoutant un [ \<liaison >](../../../../docs/framework/misc/binding.md) à la [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) et en définissant le `name` attribut.  
  
    3.  Spécifier un mode d’authentification et de la version des spécifications WS-Security qui sont utilisés pour sécuriser les messages qui sont compatibles avec WSE 3.0, en ajoutant un enfant [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) à la [ \<liaison >](../../../../docs/framework/misc/binding.md).  
  
         Pour définir le mode d’authentification, définissez la `authenicationMode` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Un mode d'authentification équivaut approximativement à une assertion de sécurité clés en main dans WSE 3.0. Le tableau suivant mappe des modes d'authentification dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aux assertions de sécurité clés en main dans WSE 3.0.  
  
        |Mode d'authentification WCF|Assertion de sécurité clé en main de WSE 3.0|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         \*Une des principales différences entre le `mutualCertificate10Security` et `mutualCertificate11Security` les assertions de sécurité clé en main est la version de la spécification WS-Security utilisée par WSE pour sécuriser les messages SOAP. Pour `mutualCertificate10Security`, la version 1.0 de WS-Security est utilisée tandis que c'est la version 1.1 de WS-Security qui est utilisée pour `mutualCertificate11Security`. Pour [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], la version de la spécification WS-Security est spécifiée dans le `messageSecurityVersion` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Pour définir la version de la spécification WS-Security qui est utilisée pour sécuriser les messages SOAP, définissez la `messageSecurityVersion` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md). Pour permettre l'interaction avec WSE 3.0, affectez `messageSecurityVersion` à la valeur de l'attribut <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.  
  
    4.  Indiquer que la version d’août 2004 de la spécification WS-Addressing est utilisée par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en ajoutant un [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) et définir le `messageVersion` à sa valeur à <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.  
  
        > [!NOTE]
        >  Lorsque vous utilisez SOAP 1.2, affectez à l'attribut `messageVersion` la valeur <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2.  Spécifiez que le service utilise la liaison personnalisée.  
  
    1.  Définir le `binding` attribut de la [ \<point de terminaison >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) élément `customBinding`.  
  
    2.  Définir le `bindingConfiguration` attribut de la [ \<point de terminaison >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) élément à la valeur spécifiée dans le `name` attribut de la [ \<liaison >](../../../../docs/framework/misc/binding.md) personnalisée du liaison.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, `Service.HelloWorldService` utilise une liaison personnalisée pour interagir avec les clients WSE 3.0. La liaison personnalisée spécifie que la version d'août 2004 de la spécification WS-Addressing et que la version 1.1 de WS-Security sont utilisées pour encoder les messages échangés. Les messages sont sécurisés à l'aide du mode d'authentification <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        behaviorConfiguration="ServiceBehavior"   
        name="Service.HelloWorldService">  
        <endpoint binding="customBinding" address=""  
          bindingConfiguration="ServiceBinding"  
          contract="Service.IHelloWorld"></endpoint>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="ServiceBinding">  
          <security authenticationMode="AnonymousForCertificate"  
                  messageProtectionOrder="SignBeforeEncrypt"  
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"  
                  requireDerivedKeys="false">  
          </security>  
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">  
        <serviceCredentials>  
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>  
        </serviceCredentials>  
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : personnaliser une liaison fournie par le système](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
