---
title: "4208 - RetryingSqlCommandDueToSqlError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4208 - RetryingSqlCommandDueToSqlError
## Propriétés  
  
|||  
|-|-|  
|ID|4208|  
|Mots clés|WFInstanceStore|  
|Niveau|Information|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique que le fournisseur SQL effectue une nouvelle tentative de commande SQL en raison d'une erreur SQL.  
  
## Message  
 Nouvelle tentative d'exécution d'une commande SQL en raison du numéro d'erreur SQL %1.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|ErrorNumber|xs:string|Numéro d'erreur SQL.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|