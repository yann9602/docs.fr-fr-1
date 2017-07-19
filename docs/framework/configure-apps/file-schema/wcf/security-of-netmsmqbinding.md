---
title: "&lt;security&gt; de &lt;netMsmqBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# &lt;security&gt; de &lt;netMsmqBinding&gt;
Définit les paramètres de sécurité pour une liaison MSMQ.  Elle spécifie si le transport ou la sécurité SOAP sont activés et, si c'est le cas, le mode d'authentification et les niveaux de protection utilisés.  
  
## Syntaxe  
  
```  
  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|mode|Spécifie le type de sécurité qui contrôle l'intégrité, la confidentialité et l'authentification.  Les valeurs valides sont les suivantes :<br /><br /> -   None : la sécurité est désactivée.<br />-   Transport : la protection et l'authentification sont offertes par le transport.  Cela s'applique à la sécurité des message entre les deux gestionnaires de files d'attente.  Il n'y a aucune sécurité offerte entre l'application et gestionnaire de files d'attente.  Les applications Msmq existantes sont équivalentes au niveau des fonctionnalités avec ce type de mode de sécurité.<br />-   Message : spécifie la sécurité des applications de bout en bout.  Il n'y a aucune sécurité offerte à la couche de transport.  Cette valeur est semblable à la sécurité offerte par d'autres liaisons standard.<br />-   Both : offre la sécurité à la fois à la couche de transport et à celle de messagerie SOAP.  La même information d'identification est requise pour les deux niveaux.<br /><br /> La valeur par défaut est Transport.  Cet attribut est de type <xref:System.ServiceModel.NetMsmqSecurityMode>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<message\>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|Définit le les paramètres de sécurité des messages SOAP.  Cet élément est de type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|Définit les paramètres de sécurité pour le transport MSMQ.  Cet élément est de type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|liaison|Élément de liaison du [\<netMsmqBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>   
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>   
 <xref:System.ServiceModel.NetMsmqSecurity>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)   
 [Files d'attente dans WCF](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)