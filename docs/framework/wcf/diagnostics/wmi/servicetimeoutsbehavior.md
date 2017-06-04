---
title: "ServiceTimeoutsBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceTimeoutsBehavior
ServiceTimeoutsBehavior  
  
## Syntaxe  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## Méthodes  
 La classe ServiceTimeoutsBehavior ne définit pas de méthode.  
  
## Propriétés  
 La classe ServiceTimeoutsBehavior a la propriété suivante :  
  
### TransactionTimeout  
 Type de données : datetime  
  
 Type d'accès : lecture seule  
  
 Période pendant laquelle une transaction doit s'effectuer.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>