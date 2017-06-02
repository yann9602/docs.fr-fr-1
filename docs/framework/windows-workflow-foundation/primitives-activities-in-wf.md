---
title: "Activit&#233;s de primitives dans WF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Activit&#233;s de primitives dans WF
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] offre plusieurs activités fournies par le système qui proposent un mécanisme commode pour exécuter les tâches courantes.  
  
|Activité|Description|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|Affecte une valeur à une variable au niveau de la portée actuelle.|  
|<xref:System.Activities.Statements.Delay>|Place un chemin d'exécution dans un état d'inactivité, en autorisant éventuellement le déchargement du workflow.|  
|<xref:System.Activities.Statements.InvokeDelegate>|Exécute un délégué qui dérive de <xref:System.Activities.ActivityDelegate> et est exposé en tant que propriété.|  
|<xref:System.Activities.Statements.InvokeMethod>|Exécute une méthode publique d'un objet CLR.|  
|<xref:System.Activities.Statements.WriteLine>|Écrit une chaîne spécifiée dans la console ou un objet <xref:System.IO.TextWriter> spécifié.|