---
title: "4206 - UnlockInstanceException | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 4206 - UnlockInstanceException
## Propriétés  
  
|||  
|-|-|  
|ID|4206|  
|Mots clés|WFInstanceStore|  
|Niveau|Erreur|  
|Canal|Microsoft\-Windows\-Application Server\-Applications\/Débogage|  
  
## Description  
 Indique qu'une exception s'est produite lors de la tentative de déverrouillage d'une instance.  
  
## Message  
 Exception %1 rencontrée lors de la tentative de déverrouillage de l'instance.  
  
## Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|------------------------------|-------------------------------|-----------------|  
|ExceptionMessage|xs:string|Message de l'exception SQL.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|