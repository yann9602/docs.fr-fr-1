---
title: "Comment&#160;: cr&#233;er des boutons bascule dans les contr&#244;les ToolStrip | Microsoft Docs"
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
  - "exemples (Windows Forms), barres d'outils"
  - "boutons bascule, créer"
  - "ToolStrip (contrôle Windows Forms), créer des boutons bascule"
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er des boutons bascule dans les contr&#244;les ToolStrip
Lorsqu'un utilisateur clique sur un bouton bascule, ce bouton apparaît enfoncé et conserve cet aspect jusqu'à ce que l'utilisateur clique une nouvelle fois sur le bouton.  
  
### Pour créer un ToolStripButton bascule  
  
-   Utilisez un code similaire à l'exemple de code suivant.  Ce code suppose que votre formulaire contient un contrôle <xref:System.Windows.Forms.ToolStrip>, ainsi que sa collection <xref:System.Windows.Forms.ToolStrip.Items%2A> contient une classe <xref:System.Windows.Forms.ToolStripButton> appelée `toolStripButton1`.  Il suppose également que vous utilisez un gestionnaire d'événements appelé `toolStripButton1_CheckedChanged`.  
  
     \[Visual Basic\]  
  
    ```  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripButton>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)