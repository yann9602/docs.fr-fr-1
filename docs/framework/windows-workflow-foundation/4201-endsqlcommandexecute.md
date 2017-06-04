---
title: "4201 - EndSqlCommandExecute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 4201 - EndSqlCommandExecute
## Propriétés  
  
|||  
|-|-|  
|ID|4201|  
|Mots clés|WFInstanceStore|  
|Niveau|Verbose|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique que l'exécution d'une commande SQL est terminée.  
  
## Message  
 Fin de l'exécution de la commande SQL : %1  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|SqlCommand|xs:string|Commande SQL exécutée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|