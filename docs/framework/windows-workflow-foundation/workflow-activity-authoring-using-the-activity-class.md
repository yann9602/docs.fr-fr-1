---
title: "Cr&#233;ation de l&#39;activit&#233; de workflow &#224; l&#39;aide de la classe d&#39;activit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Cr&#233;ation de l&#39;activit&#233; de workflow &#224; l&#39;aide de la classe d&#39;activit&#233;
La méthode la plus simple pour créer une activité à l'aide de [!INCLUDE[wf](../../../includes/wf-md.md)] dans [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] est de créer une classe qui hérite de <xref:System.Activities.Activity> qui crée les fonctionnalités en assemblant des activités personnalisées ou des activités du [Bibliothèque d'activités intégrée](../../../docs/framework/windows-workflow-foundation//net-framework-4-5-built-in-activity-library.md).Cette rubrique montre comment créer une activité qui écrit deux messages sur la console.  
  
### Pour créer une activité personnalisée à l'aide du concepteur d'activités  
  
1.  Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Sélectionnez Fichier, Nouveau, puis Projet.Sélectionnez **Workflow 4.0** sous **Visual C\#** dans la fenêtre **Types de projet**, puis sélectionnez le nœud **v2010**.Sélectionnez **Bibliothèque d'activités** dans la fenêtre **Modèles**.Nommez le nouveau projet HelloActivity.  
  
3.  Ouvrez la nouvelle activité.Faites glisser une activité <xref:System.Activities.Statements.Sequence> de la boîte à outils jusqu'à l'aire du concepteur.  
  
4.  Faites glisser une activité <xref:System.Activities.Statements.WriteLine> dans l'activité <xref:System.Activities.Statements.Sequence>.Entrez `"Hello World"` \(avec des guillemets\) dans le champ **Texte**.  
  
5.  Faites glisser une deuxième activité <xref:System.Activities.Statements.WriteLine> dans l'activité <xref:System.Activities.Statements.Sequence>, en dessous de la première.Entrez `"Goodbye"` \(avec des guillemets\) dans le champ **Texte**.