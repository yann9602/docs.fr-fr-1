---
title: "Comment&#160;: activer la r&#233;organisation des &#233;l&#233;ments ToolStrip au moment de l&#39;ex&#233;cution dans les Windows Forms | Microsoft Docs"
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
  - "AllowItemReorder (propriété)"
  - "exemples (Windows Forms), barres d'outils"
  - "barres d'outils (Windows Forms), réordonner les contrôles"
  - "ToolStrip (contrôle Windows Forms), exemples"
  - "ToolStrip (contrôle Windows Forms), réorganiser les éléments"
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: activer la r&#233;organisation des &#233;l&#233;ments ToolStrip au moment de l&#39;ex&#233;cution dans les Windows Forms
Vous pouvez autoriser l'utilisateur à réorganiser les contrôles <xref:System.Windows.Forms.ToolStripItem> au niveau de <xref:System.Windows.Forms.ToolStrip>.  
  
### Pour activer la réorganisation ToolStripItem au moment de l'exécution  
  
-   Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> la valeur `true`.  Par défaut, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> a la valeur `false`.  
  
     Au moment de l'exécution, l'utilisateur maintient la touche ALT et le bouton gauche de la souris enfoncés pour faire glisser un élément <xref:System.Windows.Forms.ToolStripItem> vers un emplacement différent de <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)