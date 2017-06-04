---
title: "&lt;mtomMessageEncoding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# &lt;mtomMessageEncoding&gt;
Spécifie l'encodage et le suivi des versions de message utilisés pour les messages basés sur MTOM \(Message Transmission Optimization Mechanism\).  
  
## Syntaxe  
  
```  
  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding=”UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|maxBufferSize|Entier qui spécifie la taille maximale de la mémoire tampon qui peut être utilisée.|  
|maxReadPoolSize|Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.  Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.  La valeur par défaut est 64.|  
|maxWritePoolSize|Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.  Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.  La valeur par défaut est 16.|  
|messageVersion|Spécifie la version SOAP des messages envoyés à l'aide de la liaison.  Les valeurs valides sont les suivantes :<br /><br /> -   Soap11Addressing1<br />-   Soap12Addressing10<br /><br /> La valeur par défaut est Soap12Addressing10.  Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.  Les valeurs valides sont les suivantes :<br /><br /> -   UnicodeFffeTextEncoding : encodage Unicode Big Endian<br />-   Utf16TextEncoding : encodage Unicode<br />-   Utf8TextEncoding : encodage 8 bits<br /><br /> La valeur par défaut est Utf8TextEncoding.  Cet attribut est de type <xref:System.Text.Encoding>.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas\>](../Topic/%3CreaderQuotas%3E.md)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.  Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 L'encodage est le processus de transformation d'un message en une séquence d'octets.  Le décodage est le processus inverse.  Windows Communication Foundation \(WCF\) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM \(Message Transmission Optimization Mechanism\).  
  
 L'élément `MtomMessageEncoding` spécifie l'encodage de caractères et le contrôle de version de message, ainsi que d'autres paramètres utilisés pour un message encodé avec MTOM \(Message Transmission Optimization Mechanism\).  MTOM est une technologie efficace de transmission de données binaires dans les messages WCF.  L'encodeur MTOM tente de créer un équilibre entre rendement et interopérabilité.  L'encodage MTOM transmet la plupart des données XML sous forme textuelle, mais optimise les blocs de données binaires volumineux en les transmettant tels quels, sans conversion au format base64 encodé.  
  
## Exemple  
  
```  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion=”Soap11Addressing10”  
    textEncoding=”utf-8” />  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>   
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>   
 [Encodage de message](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)   
 [Sélection d'un encodeur de message](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)