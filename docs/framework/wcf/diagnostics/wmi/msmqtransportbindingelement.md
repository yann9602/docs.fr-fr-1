---
title: "MsmqTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## Syntaxe  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## Méthodes  
 La classe MsmqTransportBindingElement ne définit pas de méthode.  
  
## Propriétés  
 La classe MsmqTransportBindingElement a les propriétés suivantes :  
  
### MaxPoolSize  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Taille maximale du pool contenant des objets de message MSMQ internes.  
  
### QueueTransferProtocol  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur d'énumération qui indique le transport de canal de communication mis en file d'attente que cette liaison utilise.  
  
### UseActiveDirectory  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Renvoie une valeur booléenne qui indique si des adresses de file d'attente doivent être converties à l'aide d'Active Directory.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>