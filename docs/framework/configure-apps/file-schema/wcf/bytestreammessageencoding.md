---
title: "&lt;byteStreamMessageEncoding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;byteStreamMessageEncoding&gt;
Spécifie l'encodage de message sous forme de flux d'octets, avec l'option permettant de spécifier l'encodage de caractères.  
  
## Syntaxe  
  
```  
  
<byteStreamMessageEncoding/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|messageVersion|Spécifie la version SOAP des messages envoyés à l'aide de la liaison.  Cette propriété ne peut être affectée que de la valeur de version de message <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.  L'encodeur de message en flux d'octets ne prend pas en charge d'autres versions de message.<br /><br /> Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>   
 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>   
 [Encodage de message](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)   
 [Sélection d'un encodeur de message](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)