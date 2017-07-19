---
title: "4209 - TimeoutOpeningSqlConnection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4209 - TimeoutOpeningSqlConnection
## Propriétés  
  
|||  
|-|-|  
|ID|4209|  
|Mots clés|WFInstanceStore|  
|Niveau|Erreur|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une expiration de délai d'attente s'est produite lors de la tentative d'ouverture d'une connexion SQL.  
  
## Message  
 Expiration du délai d'attente lors de la tentative d'ouverture d'une connexion SQL.  L'opération ne s'est pas terminée dans le délai imparti de %1.  Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|Délai d'expiration|xs:string|Valeur de délai d'attente pour ouvrir la connexion SQL.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|