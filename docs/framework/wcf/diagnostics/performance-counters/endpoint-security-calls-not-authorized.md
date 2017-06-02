---
title: "Point de terminaison&#160;: appels de s&#233;curit&#233; non autoris&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# Point de terminaison&#160;: appels de s&#233;curit&#233; non autoris&#233;s
Nom du compteur : Appels de sécurité non autorisés.  
  
## Description  
 Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.  Il indique que le message entrant provient d'un utilisateur valide et qu'il est correctement protégé, mais que l'utilisateur n'est pas autorisé à exécuter des tâches spécifiques.