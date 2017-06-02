---
title: "ActivityTransfer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ActivityTransfer
Événement du transfert de l'activité  
  
## Syntaxe  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## Méthodes  
 La classe ActivityTransfer ne définit pas de méthode.  
  
## Propriétés  
 La classe ActivityTransfer a les propriétés suivantes :  
  
### ActivityID  
  
-   Type de données : objet                   
     Type d'accès : lecture seule  
  
-   ID d'activité  
  
### RelatedActivityID  
  
-   Type de données : objet                   
     Type d'accès : lecture seule  
  
-   ID d'activité connexe  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel.|