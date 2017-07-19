---
title: "ServiceThrottlingBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## Syntaxe  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## Méthodes  
 La classe ServiceThrottlingBehavior ne définit pas de méthode.  
  
## Propriétés  
 La classe ServiceThrottlingBehavior a les propriétés suivantes :  
  
### MaxConcurrentCalls  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de messages en cours de traitement actif sur tous les objets de répartiteur dans un ServiceHost.  
  
### MaxConcurrentInstances  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal d'objets de service simultanément exécutables.  
  
### MaxConcurrentSessions  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 Nombre maximal de sessions qu'un hôte peut accepter à la fois.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>