---
title: "&lt;oneWay&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;oneWay&gt;
Active le routage de paquets et l'utilisation de méthodes unidirectionnelles pour une liaison personnalisée.  
  
## Syntaxe  
  
```  
  
<oneWay packetRoutable="Boolean">  
        <channelPoolSettings  
           idleTimeout"TimeSpan"  
          leaseTimeout"TimeSpan"  
          maxOutboundConnectionsPerEndpopint=”Integer” />  
```  
  
```  
  
</oneWay>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`packetRoutable`|Valeur booléenne qui spécifie si le routage de paquets est activé.  La valeur par défaut est `false`.|  
|`MaxAcceptedChannels`|Entier qui spécifie le nombre maximal de canaux qui peuvent être acceptés.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<channelPoolSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/channelpoolsettings.md)|Objet <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> qui contient des propriétés du pool de canaux pour le canal actuel.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<liaison\>](../../../../../docs/framework/misc/binding.md)|Définit toutes les fonctions de liaison d'une liaison personnalisée.|  
  
## Notes  
 Pour activer le routage de paquets, une couche de conversion unidirectionnelle est nécessaire \(fournie par cet élément\).  Un utilisateur peut créer une liaison personnalisée qui crée une couche pour cette liaison via un transport prenant en charge la session ou de type demande\/réponse pour qu'elle puisse router les paquets.  Cet élément s'avère également utile lorsque vous souhaitez exposer des méthodes unidirectionnelles de façon plus native.  D'autres transformations peuvent être appliquées sur cette couche, comme le duplex composite et la messagerie fiable.  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>   
 <xref:System.ServiceModel.Configuration.OneWayElement>   
 <xref:System.ServiceModel.Channels.CustomBinding>   
 [Liaisons](../../../../../docs/framework/wcf/bindings.md)   
 [Extension de liaisons](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Liaisons personnalisées](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)