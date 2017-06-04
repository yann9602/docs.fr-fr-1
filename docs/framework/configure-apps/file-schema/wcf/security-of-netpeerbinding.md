---
title: "&lt;security&gt; de &lt;netPeerBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# &lt;security&gt; de &lt;netPeerBinding&gt;
Définit les paramètres de sécurité de [\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), y compris le type d'authentification utilisé et la sécurité utilisée pour le transport de messages.  
  
## Syntaxe  
  
```  
  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|mode|Facultatif.  Spécifie le type de sécurité utilisé par les homologues configurés avec cette liaison.  La valeur par défaut est `Message`.  Cet attribut est de type <xref:System.ServiceModel.SecurityMode>.|  
  
## Attribut Mode  
  
|Valeur|Description|  
|------------|-----------------|  
|Message|La sécurité SOAP assure l'authentification, l'intégrité et la confidentialité.|  
|None|La sécurité est désactivée.|  
|Transport|La sécurité est fournie à l'aide de HTTPS.|  
|TransportWithMessageCredential|Le protocole HTTPS assure l'authentification et la confidentialité.  Les messages SOAP fournissent des types d'informations d'identification enrichies.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<transport\>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|Définit le type de transport pour les messages sécurisés envoyés par des homologues configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison de [\<netPeerTcpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).|  
  
## Notes  
 La sécurité peut être spécifique au message ou au transport.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>   
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>   
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>   
 <xref:System.ServiceModel.PeerSecuritySettings>   
 [Sécurisation des services et des clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Sélection d'un type d'informations d'identification](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Configuration des liaisons fournies par le système](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/fr-fr/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<liaison\>](../../../../../docs/framework/misc/binding.md)