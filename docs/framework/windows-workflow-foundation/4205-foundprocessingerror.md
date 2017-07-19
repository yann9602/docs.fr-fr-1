---
title: "4205 - FoundProcessingError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2235a15-dd87-439e-8cb9-8b1b89a3dacf
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4205 - FoundProcessingError
## Propriétés  
  
|||  
|-|-|  
|ID|4205|  
|Mots clés|WFInstanceStore|  
|Niveau|Erreur|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique que la commande du fournisseur SQL a échoué.  
  
## Message  
 Échec de la commande : %1  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|ExceptionMessage|xs:string|Message de l'exception SQL.|  
|Exception|xs:string|Détails de l'exception|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|