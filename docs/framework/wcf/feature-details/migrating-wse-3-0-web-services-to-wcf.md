---
title: Migration des services Web WSE 3.0 vers WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c97279b553a615feda1dd3a195ad033744d82983
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migration des services Web WSE 3.0 vers WCF
Les avantages liés à la migration des services Web WSE 3.0 vers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] incluent l'amélioration des performances et la prise en charge de transports supplémentaires, de scénarios de sécurité supplémentaires et des spécifications WS-*. Un service Web migré à partir de WSE 3.0 vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut présenter une amélioration des performances comprise entre 200 % et 400 %. Pour plus d’informations sur les transports pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [choisir un Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Pour obtenir la liste des scénarios pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [des scénarios de sécurité courants](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Pour obtenir la liste des spécifications qui sont pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Guide de l’interopérabilité de protocoles de Services Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Les sections suivantes fournissent une aide sur la manière de migrer une fonctionnalité spécifique d'un service Web WSE 3.0 vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="general"></a>Général  
 Les applications WSE 3.0 et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] incluent une interopérabilité au niveau du câble et un ensemble commun de terminologie. Les applications WSE 3.0 et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont interopérables au niveau du câble en fonction de l'ensemble de spécifications WS-* qu'elles prennent en charge. Lorsqu'une application WSE 3.0 ou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est développée, il existe un ensemble commun de terminologie, telle que les noms des assertions de sécurité clé en main dans WSE et les modes d'authentification.  
  
 Bien qu'il y ait de nombreux aspects semblables entre les modèles de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et ASP.NET ou WSE 3.0, ils sont différents. Pour plus d’informations sur la [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modèle de programmation, consultez [cycle de vie de programmation base](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  Pour migrer un service Web WSE vers WCF le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil peut être utilisé pour générer un client. Ce client contient des interfaces et des classes qui peuvent être utilisées également comme point de départ pour un service WCF. Les interfaces générées ont l'attribut <xref:System.ServiceModel.OperationContractAttribute> appliqué aux membres du contrat avec la propriété <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> définie à `*`. Lorsqu’un client WSE appelle un service Web avec ce paramètre, l’exception suivante est levée : **Web.Services3.ResponseProcessingException : WSE910 : une erreur s’est produite lors du traitement d’un message de réponse, et vous trouverez l’erreur en interne exception**. À des fins d'atténuation, affectez à la propriété <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> de l'attribut <xref:System.ServiceModel.OperationContractAttribute> une valeur non `null`, telle que `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Sécurité  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Services Web WSE 3.0 sécurisés à l'aide d'un fichier de stratégie  
 Les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent utiliser un fichier de configuration pour sécuriser un service ; ce mécanisme s'apparente à un fichier de stratégie WSE 3.0. Dans WSE 3.0, lorsque vous sécurisez un service Web à l'aide d'un fichier de stratégie, vous utilisez une assertion de sécurité clé en main ou une assertion de stratégie personnalisée. Les assertions de sécurité clé en main sont mappées étroitement au mode d'authentification d'un élément de liaison de sécurité [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Les modes d'authentification [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et les assertions de sécurité clé en main WSE 3.0 sont non seulement nommés de manière identique ou similaire, mais ils sécurisent les messages à l'aide des mêmes types d'informations d'identification. Par exemple, l'assertion de sécurité clé en main `usernameForCertificate` dans WSE 3.0 mappe au mode d'authentification `UsernameForCertificate` dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Les exemples de code suivants montrent comment une stratégie minimale qui utilise l'assertion de sécurité clé en main `usernameForCertificate` dans WSE 3.0 mappe à un mode d'authentification `UsernameForCertificate` dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dans une liaison personnalisée.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Pour migrer les paramètres de sécurité d'un service Web WSE 3.0 spécifiés dans un fichier de stratégie vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], une liaison personnalisée doit être créée dans un fichier de configuration et l'assertion de sécurité clé en main doit avoir pour valeur son mode d'authentification équivalent. En outre, la liaison personnalisée doit être configurée de façon à utiliser la spécification WS-Addressing d'août 2004 lorsque des clients WSE 3.0 communiquent avec le service. Lorsque le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] migré ne nécessite pas de communication avec des clients WSE 3.0 et doit uniquement maintenir la parité de sécurité, envisagez d'utiliser les liaisons définies par le système [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec les paramètres de sécurité appropriés au lieu de créer une liaison personnalisée.  
  
 Le tableau suivant répertorie le mappage entre un fichier de stratégie WSE 3.0 et la liaison personnalisée équivalente dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Assertion de sécurité clé en main WSE 3.0|Configuration de liaison personnalisée WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Pour plus d’informations sur la création de liaisons personnalisées dans WCF, consultez [des liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Services Web WSE 3.0 sécurisés à l'aide du code d'application  
 Que WSE 3.0 ou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] soit utilisé, les conditions de sécurité peuvent être spécifiées dans le code d'application plutôt que dans la configuration. Dans WSE 3.0, cette tâche est accomplie en créant une classe qui dérive de la classe `Policy`, puis en ajoutant les spécifications en appelant la méthode `Add`. Pour plus d’informations sur la spécification des exigences de sécurité dans le code, consultez [Comment : sécuriser un Service Web sans utiliser un fichier de stratégie](http://go.microsoft.com/fwlink/?LinkId=73747). Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], pour spécifier des conditions de sécurité dans le code, créez une instance de la classe <xref:System.ServiceModel.Channels.BindingElementCollection> et ajoutez une instance d'un <xref:System.ServiceModel.Channels.SecurityBindingElement> au <xref:System.ServiceModel.Channels.BindingElementCollection>. Les spécifications de l'assertion de sécurité sont définies à l'aide des méthodes d'assistance de mode d'authentification statiques de la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>. Pour plus d’informations sur la spécification des exigences de sécurité à l’aide de code [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : créer un personnalisé de liaison à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) et [Comment : créer un SecurityBindingElement pour un Spécifié le Mode d’authentification](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Assertion de stratégie personnalisée WSE 3.0  
 Dans WSE 3.0, il existe deux types d'assertions de stratégie personnalisées : celles qui sécurisent un message SOAP et celles qui ne le font pas. Les assertions de stratégie qui sécurisent les messages SOAP dérivent de la classe `SecurityPolicyAssertion` WSE 3.0 et l'équivalent conceptuel dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est la classe <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Il convient de noter que les assertions de sécurité clé en main WSE 3.0 sont un sous-ensemble des modes d'authentification [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Si vous avez créé une assertion de stratégie personnalisée dans WSE 3.0, il peut exister un mode d'authentification [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] équivalent. Par exemple, WSE 3.0 ne fournit pas d'assertion de sécurité CertificateOverTransport qui équivaut à l'assertion de sécurité clé en main `UsernameOverTransport`, mais il utilise un certificat X.509 à des fins d'authentification du client. Si vous avez défini votre propre assertion de stratégie personnalisée pour ce scénario, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] facilite grandement la migration. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] définit un mode d'authentification pour ce scénario, ce qui vous permet de tirer parti des méthodes d'assistance de mode d'authentification statiques pour configurer un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Lorsqu'il n'existe pas de mode d'authentification [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] équivalent à une assertion de stratégie personnalisée qui sécurise les messages SOAP, dérivez une classe des classes <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et spécifiez l'élément de liaison équivalent. Pour plus d’informations, consultez [Comment : créer un personnalisé de liaison à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Pour convertir une assertion de stratégie personnalisée qui ne sécurise pas un message SOAP, consultez [filtrage](../../../../docs/framework/wcf/feature-details/filtering.md) et l’exemple [intercepteur de Message personnalisé](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Jeton de sécurité personnalisé WSE 3.0  
 Le modèle de programmation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permettant de créer un jeton personnalisé diffère de WSE 3.0. Pour plus d’informations sur la création d’un jeton personnalisé dans WSE, consultez [création des jetons de sécurité personnalisés](http://go.microsoft.com/fwlink/?LinkID=73750). Pour plus d’informations sur la création d’un jeton personnalisé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>Gestionnaire de jetons personnalisés WSE 3.0  
 Le modèle de programmation permettant de créer un gestionnaire de jetons personnalisés diffère entre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et WSE 3.0. Pour plus d’informations sur la création d’un gestionnaire de jetons personnalisés et les autres composants requis pour un jeton de sécurité personnalisé, consultez [Comment : créer un jeton personnalisé](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Si vous avez créé un gestionnaire de jetons de sécurité `UsernameToken` personnalisés, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit un mécanisme plus simple pour spécifier la logique d'authentification que la création d'un gestionnaire de jetons de sécurité personnalisés. Pour plus d’informations, consultez [Comment : utiliser un validateur de mot de passe et un nom d’utilisateur personnalisé](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Services Web WSE 3.0 qui utilisent des messages SOAP encodés MTOM  
 Comme une application WSE 3, une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut spécifier l'encodage de message MTOM dans la configuration. Pour migrer ce paramètre, vous devez ajouter le [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) à la liaison pour le service. L'exemple de code suivant montre comment l'encodage MTOM est spécifié dans WSE 3.0 pour un service qui est équivalent dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Messagerie  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Applications WSE 3.0 qui utilisent l'API de messagerie WSE  
 Lorsque l'API de messagerie WSE est utilisée pour obtenir un accès direct au XML communiqué entre le client et le service Web, l'application peut être convertie de façon à utiliser le « Plain Old XML » (POX). Pour plus d’informations sur POX, consultez [l’interopérabilité avec les Applications POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Pour plus d’informations sur l’API de messagerie WSE, consultez [envoi et réception de Messages à l’aide de WSE messagerie API SOAP](http://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Transports  
  
### <a name="tcp"></a>TCP  
 Par défaut, les services Web et les clients WSE 3.0 qui envoient des messages SOAP à l'aide du transport TCP n'interagissent pas avec les services Web et les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Cette incompatibilité est due aux différences de tramage utilisé dans le protocole TCP et aux performances. Toutefois, un exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] décrit comment implémenter une session TCP personnalisée qui interagit avec WSE 3.0. Pour plus d’informations sur cet exemple, consultez [Transport : WSE 3.0 TCP Interoperability](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Pour spécifier qu’un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application utilise le transport TCP, utilisez le [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Transport personnalisé  
 L'équivalent d'un transport personnalisé WSE 3.0 dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est une extension de canal. Pour plus d’informations sur la création d’une extension de canal, consultez [extension de la couche de canal](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Cycle de vie de la programmation de base](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Comment : créer une liaison personnalisée à l’aide de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Comment : créer un SecurityBindingElement pour un Mode d’authentification spécifié](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
