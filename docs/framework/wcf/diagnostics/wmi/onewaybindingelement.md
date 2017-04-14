---
title: "OneWayBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# OneWayBindingElement
OneWayBindingElement  
  
## Syntaxe  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## Méthodes  
 La classe OneWayBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe OneWayBindingElement a les propriétés suivantes :  
  
### ChannelPoolSettings  
 Type de données : ChannelPoolSettings  
  
 Type d'accès : lecture seule  
  
 Paramètres du pool de canaux.  
  
### MaxAcceptedChannels  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de canaux acceptés.  
  
### PacketRoutable  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui indique si le paquet peut être routé.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>