---
title: "WSAT_TraceRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# WSAT_TraceRecord
WSAT\_TraceRecord  
  
## Syntaxe  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## Méthodes  
 La classe WSAT\_TraceRecord ne définit aucune méthode.  
  
## Propriétés  
 La classe WSAT\_TraceRecord a les propriétés suivantes :  
  
### ActivityID  
 Type de données : objet  
Type d'accès : lecture seule  
  
 ID d'activité de l'enregistrement de suivi.  
  
### EventID  
 Type de données : sint32  
Type d'accès : lecture seule  
  
 ID d'événement de l'enregistrement de suivi.  
  
### TraceRecord  
 Type de données : chaîne  
Type d'accès : lecture seule  
  
 Enregistrement de suivi  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|