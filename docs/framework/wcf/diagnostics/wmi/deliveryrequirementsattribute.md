---
title: "DeliveryRequirementsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## Syntaxe  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## Méthodes  
 La classe DeliveryRequirementsAttribute ne définit pas de méthodes.  
  
## Propriétés  
 La classe DeliveryRequirementsAttribute a les propriétés suivantes :  
  
### QueuedDeliveryRequirements  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Spécifie si la liaison pour un service prend en charge des contrats.  
  
### RequireOrderedDelivery  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Spécifie si la liaison prend en charge les messages ordonnés.  
  
### TargetContract  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Contrat auquel il s'applique.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>