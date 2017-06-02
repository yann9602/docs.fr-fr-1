---
title: "Vue d&#39;ensemble du contr&#244;le ToolStripContainer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ToolStripContainer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "barres d'outils (Windows Forms), rafting intégré"
  - "ToolStripContainer (contrôle Windows Forms), à propos du contrôle ToolStripContainer"
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Vue d&#39;ensemble du contr&#244;le ToolStripContainer
Un <xref:System.Windows.Forms.ToolStripContainer> a des panneaux sur ses chacun de ses quatre côtés pour le positionnement et le rafting des contrôles <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.StatusStrip>.  Plusieurs contrôles <xref:System.Windows.Forms.ToolStrip> s'empilent verticalement si vous les placez dans le <xref:System.Windows.Forms.ToolStripContainer> gauche ou droit.  Ils s'empilent horizontalement si vous les placez dans le <xref:System.Windows.Forms.ToolStripContainer> supérieur ou inférieur.  Vous pouvez utiliser le <xref:System.Windows.Forms.ToolStripContentPanel> central du <xref:System.Windows.Forms.ToolStripContainer> pour positionner les contrôles traditionnels sur le formulaire.  
  
 Un ou tous les contrôles <xref:System.Windows.Forms.ToolStripContainer> sont directement sélectionnables au moment du design et peuvent être supprimés.  Vous pouvez développer et réduire chaque panneau d'un <xref:System.Windows.Forms.ToolStripContainer>. De plus, ce dernier se redimensionne en fonction des contrôles qu'il contient.  
  
### Membres ToolStripContainer importants  
  
|Nom|Description|  
|---------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|Obtient le panneau inférieur de <xref:System.Windows.Forms.ToolStripContainer>.|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|Obtient ou définit une valeur indiquant si le panneau inférieur de <xref:System.Windows.Forms.ToolStripContainer> est visible.|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|Obtient le panneau gauche de <xref:System.Windows.Forms.ToolStripContainer>.|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|Obtient ou définit une valeur indiquant si le panneau gauche de <xref:System.Windows.Forms.ToolStripContainer> est visible.|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|Obtient le panneau droit de <xref:System.Windows.Forms.ToolStripContainer>.|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|Obtient ou définit une valeur indiquant si le panneau droit de <xref:System.Windows.Forms.ToolStripContainer> est visible.|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|Obtient le panneau supérieur de <xref:System.Windows.Forms.ToolStripContainer>.|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|Obtient ou définit une valeur indiquant si le panneau supérieur de <xref:System.Windows.Forms.ToolStripContainer> est visible.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripContainer>   
 <xref:System.Windows.Forms.ToolStripContentPanel>