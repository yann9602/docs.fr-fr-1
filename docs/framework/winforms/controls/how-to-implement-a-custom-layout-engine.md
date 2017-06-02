---
title: "Comment&#160;: impl&#233;menter un moteur de pr&#233;sentation personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "FlowLayoutPanel (contrôle Windows Forms), moteur de présentation"
  - "moteurs de présentation, personnalisé"
  - "moteurs de présentation, implémenter"
  - "LayoutEngine (classe)"
  - "TableLayoutPanel (contrôle Windows Forms), moteur de présentation"
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: impl&#233;menter un moteur de pr&#233;sentation personnalis&#233;
L'exemple de code suivant montre comment créer un moteur de présentation personnalisé qui exécute une mise en page fluide et simple.  Il implémente un contrôle Panel nommé `DemoFlowPanel` qui substitue la propriété <xref:System.Windows.Forms.Control.LayoutEngine%2A> pour fournir une instance de la classe `DemoFlowLayout`.  
  
## Exemple  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## Voir aussi  
 <xref:System.Windows.Forms.Layout.LayoutEngine>   
 <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=fullName>