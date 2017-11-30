---
title: '&lt;webMessageEncoding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e6257721f8b85296d4da28cc036c946f6357c11b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebmessageencodinggt"></a>&lt;webMessageEncoding&gt;
Permet de lire et d'écrire du contenu XML en texte brut, les encodages de message JSON (JavaScript Objet Notation) et du contenu binaire brut dans une liaison [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
 \<system.serviceModel >  
\<liaisons >  
\<customBinding >  
\<liaison >  
\<webMessageEncoding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webMessageEncoding   
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
  
writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`maxReadPoolSize`|Quantité maximale de messages pouvant être consultés simultanément sans allouer de nouveaux lecteurs. Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse. La valeur par défaut est de 64 lecteurs par encodeur interne (texte, JSON, et « brut »).<br /><br /> L'augmentation de ce nombre entraîne celle de la consommation de mémoire, mais prépare l'encodeur afin de traiter les rafales soudaines de messages entrants. En effet, il peut ainsi utiliser les lecteurs existants du pool au lieu d'en créer.|  
|`maxWritePoolSize`|Quantité maximale de messages pouvant être envoyés simultanément sans allouer de nouveaux enregistreurs. Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse. La valeur par défaut est de 16 enregistreurs par encodeur interne (texte, JSON, et « brut »).<br /><br /> L'augmentation de ce nombre entraîne celle de la consommation de mémoire, mais prépare l'encodeur afin de traiter les rafales soudaines de messages sortants. En effet, il peut ainsi utiliser les writers existants du pool au lieu d'en créer.|  
|`writeEncoding`|Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison. Les valeurs valides sont les suivantes :<br /><br /> -UnicodeFffeTextEncoding : Encodage Unicode Big Endian.<br />-Utf16TextEncoding : L’encodage Unicode.<br />-Utf8TextEncoding : encodage de 8 bits.<br /><br /> La valeur par défaut est Utf8TextEncoding. Cet attribut est de type <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison. Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison >](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Remarques  
 L'encodage est le processus de transformation d'un message en une séquence d'octets. Le décodage est le processus inverse. Ces processus nécessitent l'encodage de caractères à titre de spécification.  
  
 L'élément `webMessageEncoding` fonctionne par délégation à une série d'encodeurs internes afin de gérer les données XML de texte brut, les encodages JSON et les données binaires brutes. Cette délégation a lieu par le biais d'un encodeur de message composite.  
  
 Cet élément de liaison et son encodeur composite sont utilisés pour contrôler l'encodage dans des scénarios qui n'utilisent pas la messagerie SOAP utilisée par l'élément `webHttpBinding`. Ces scénarios incluent les protocoles POX (Plain Old XML) et REST (Representational State Transfer), la syndication RSS (Really Simple Syndication) et Atom, ainsi que le protocole AJAX (Asynchronous JavaScript and XML). L'encodeur de messages composite ne prend pas en charge SOAP ni WS-Addressing.  
  
 L'élément de liaison peut être configuré avec un encodage de caractères d'écriture à l'aide de l'attribut `writeEncoding`. La valeur <xref:System.Text.Encoding> fournie spécifie le comportement sur l'écriture pour les cas JSON et XML textuels. Lors de la lecture, tous les encodages de texte et de message valides sont maîtrisés.  
  
 `maxReadPoolSize` et `maxWritePoolSize` peuvent également être utilisés pour définir respectivement le nombre maximal de lecteurs et de writers à allouer. Par défaut, 64 lecteurs et 16 writers sont alloués.  
  
 Contraintes de complexité par défaut sont également définies à l’aide de la [ \<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd) élément pour vous protéger contre une classe d’attaques de déni de service (DOS) qui tentent d’exploiter la complexité des messages pour bloquer le traitement de point de terminaison des attaques ressources.  
  
## <a name="example"></a>Exemple  
  
```xml  
<webMessageEncoding   
    maxReadPoolSize="256"  
    maxWritePoolSize="128"  
    messageVersion="None"  
    textEncoding="utf-8"   
/>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Encodage de message](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Choix d’un encodeur de Message](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)  
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
