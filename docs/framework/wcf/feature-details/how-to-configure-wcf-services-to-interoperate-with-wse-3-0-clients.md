---
title: "Comment&#160;: configurer les services WCF pour interagir avec les clients WSE&#160;3.0 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: configurer les services WCF pour interagir avec les clients WSE&#160;3.0
Les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sont compatibles au niveau câble avec les services Web Services Enhancements 3.0 for Microsoft .NET \(WSE\) lorsque les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont configurés pour utiliser la version d'août 2004 de la spécification WS\-Addressing.  
  
### Pour permettre à un service WCF d'interagir avec les clients WSE 3.0  
  
1.  Définissez une liaison personnalisée pour le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
     Pour indiquer que la version d'août 2004 de la spécification WS\-Addressing est utilisée pour l'encodage des messages, il est nécessaire de créer une liaison personnalisée.  
  
    1.  Ajoutez un [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) enfant au [\<liaisons\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) du fichier de configuration du service.  
  
    2.  Spécifiez un nom pour la liaison en ajoutant un [\<liaison\>](../../../../docs/framework/misc/binding.md) au [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) et en définissant l'attribut `name`.  
  
    3.  Spécifiez un mode d'authentification ainsi que la version des spécifications WS\-Security utilisées pour sécuriser les messages compatibles avec WSE 3.0 en ajoutant un [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) enfant au [\<liaison\>](../../../../docs/framework/misc/binding.md).  
  
         Pour définir le mode d'authentification, définissez l'attribut `authenicationMode` du [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).Un mode d'authentification équivaut approximativement à une assertion de sécurité clés en main dans WSE 3.0.Le tableau suivant mappe des modes d'authentification dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aux assertions de sécurité clés en main dans WSE 3.0.  
  
        |Mode d'authentification WCF|Assertion de sécurité clé en main de WSE 3.0|  
        |---------------------------------|--------------------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`mutualCertificate10Security`\*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`mutualCertificate11Security`\*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode>|`usernameForCertificateSecurity`|  
  
         \* L'une des principales différences entre les assertions de sécurité clé en main `mutualCertificate10Security` et `mutualCertificate11Security` réside dans la version de la spécification WS\-Security utilisée par WSE pour sécuriser les messages SOAP.Pour `mutualCertificate10Security`, la version 1.0 de WS\-Security est utilisée tandis que c'est la version 1.1 de WS\-Security qui est utilisée pour `mutualCertificate11Security`.Pour [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], la version de la spécification WS\-Security utilisée est spécifiée dans l'attribut `messageSecurityVersion` de [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Pour définir la version de la spécification WS\-Security utilisée pour sécuriser des messages SOAP, définissez l'attribut `messageSecurityVersion` de [\<sécurité\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).Pour permettre l'interaction avec WSE 3.0, affectez <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A> à la valeur de l'attribut `messageSecurityVersion`.  
  
    4.  Spécifiez que la version d'août 2004 de la spécification WS\-Addressing est utilisée par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en ajoutant un [\<textMessageEncoding\>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md), puis affectez <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A> à `messageVersion`.  
  
        > [!NOTE]
        >  Lorsque vous utilisez SOAP 1.2, affectez à l'attribut `messageVersion` la valeur <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.  
  
2.  Spécifiez que le service utilise la liaison personnalisée.  
  
    1.  Affectez la valeur `customBinding` à l'attribut `binding` de l'élément [\<Point de terminaison \(endpoint\)\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md).  
  
    2.  Affectez à l'attribut `bindingConfiguration` de l'élément [\<Point de terminaison \(endpoint\)\>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) la valeur spécifiée dans l'attribut `name` de [\<liaison\>](../../../../docs/framework/misc/binding.md) pour la liaison personnalisée.  
  
## Exemple  
 Dans l'exemple de code suivant, `Service.HelloWorldService` utilise une liaison personnalisée pour interagir avec les clients WSE 3.0.La liaison personnalisée spécifie que la version d'août 2004 de la spécification WS\-Addressing et que la version 1.1 de WS\-Security sont utilisées pour encoder les messages échangés.Les messages sont sécurisés à l'aide du mode d'authentification <xref:System.ServiceModel.Configuration.AuthenticationMode>.  
  
```  
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
  
## Voir aussi  
 [Comment : personnaliser une liaison fournie par le système](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)