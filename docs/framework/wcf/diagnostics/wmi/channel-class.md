---
title: "Channel, classe | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Channel, classe
Canal  
  
## Syntaxe  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## Méthodes  
 La classe Channel ne définit aucune méthode.  
  
## Propriétés  
 La classe Channel possède les propriétés suivantes.  
  
### LocalAddress  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Point de terminaison local du canal.  
  
### ref  
 Type de données : point de terminaison  
  
 Type d'accès : lecture seule  
  
 Référence au point de terminaison auquel le canal se connecte.  
  
### RemoteAddress  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Adresse distante associée au canal.  
  
### SessionId  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Id de session actuel, le cas échéant.  
  
### Type  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Type du canal.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.ChannelBase>