---
title: "OperationBehaviorAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# OperationBehaviorAttribute
OperationBehaviorAttribute  
  
## Syntaxe  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## Méthodes  
 La classe OperationBehaviorAttribute ne définit pas de méthodes.  
  
## Propriétés  
 La classe OperationBehaviorAttribute a les propriétés suivantes :  
  
### AutoDisposeParameters  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 État de la fonctionnalité d'élimination automatique pour les paramètres.  
  
### Emprunt d'identité  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Indique le niveau d'emprunt d'identité de l'appelant pris en charge par l'opération.  
  
### ReleaseInstanceMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Indique à quel moment il convient de recycler l'objet lors de l'appel d'une opération.  
  
### TransactionAutoComplete  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique s'il convient de valider automatiquement la transaction actuelle si aucune exception non traitée ne se produit.  
  
### TransactionScopeRequired  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si l'opération nécessite une transaction.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.OperationBehaviorAttribute>