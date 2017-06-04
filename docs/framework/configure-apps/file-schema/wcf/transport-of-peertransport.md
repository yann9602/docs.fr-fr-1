---
title: "&lt;transport&gt; de &lt;peerTransport&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;transport&gt; de &lt;peerTransport&gt;
Indique le type de transport correspondant aux messages sécurisés envoyés par des homologues configurés avec cette liaison.  
  
## Syntaxe  
  
```  
  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|credentialType|Facultatif.  Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.  Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.|  
  
## Attribut credentialType  
  
|Valeur|Description|  
|------------|-----------------|  
|Certificat|L'authentification du transport de canal homologue requiert un certificat X509.|  
|Mot de passe|L'authentification du transport de canal homologue requiert un mot de passe correct.|  
  
### Éléments enfants  
 None  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|Définit les paramètres de sécurité pour un transport d'homologue.|  
  
## Notes  
 Cet élément n'est défini que si la valeur `Transport` ou `TransportWithMessageCredential` est définie pour l'attribut de mode de [\<sécurité\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md).  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>   
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>   
 <xref:System.ServiceModel.PeerTransportSecuritySettings>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Sécurité de transport](../../../../../docs/framework/wcf/feature-details/transport-security.md)   
 [Transports](../../../../../docs/framework/wcf/feature-details/transports.md)   
 [Choix d'un transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)