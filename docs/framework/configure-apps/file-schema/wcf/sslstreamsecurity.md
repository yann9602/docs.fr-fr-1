---
title: "&lt;sslStreamSecurity&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 430a378b-a742-4858-8a12-9f9b235fd627
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# &lt;sslStreamSecurity&gt;
Représente un élément de liaison personnalisé qui prend en charge la sécurité de canal à l'aide d'un flux SSL.  
  
## Syntaxe  
  
```  
  
<sslStreamSecurity requireClientCertificate="Boolean"  
      sslProtocols="Ssl3|Tls|Tls11|Tls12" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|requireClientCertificate|Valeur booléenne qui spécifie si un certificat client est requis pour cette liaison.  La valeur par défaut est `false`.|  
|sslProtocols|Valeur d'indicateur d'énumération SslProtocols qui spécifie les protocoles SSL pris en charge.  La valeur par défaut est Ssl3&#124;Tls&#124;Tls11&#124;Tls12.|  
  
### Éléments enfants  
 Aucun\(e\).  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.SslStreamSecurityElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)