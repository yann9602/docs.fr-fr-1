---
title: "Comment&#160;: ajouter un contr&#244;le &#224; une page d&#39;onglet | Microsoft Docs"
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
  - "contrôles onglet, ordre de tabulation"
  - "pages d'onglets, ajouter des contrôles"
  - "TabPage (contrôle)"
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: ajouter un contr&#244;le &#224; une page d&#39;onglet
Vous pouvez utiliser le <xref:System.Windows.Forms.TabControl> Windows Forms pour afficher d'autres contrôles au sein d'une structure organisée.  La procédure suivante indique comment ajouter un bouton au premier onglet.  Pour plus d'informations sur l'ajout d'une icône à la partie d'étiquette d'une page d'onglets, consultez [Comment : modifier l'apparence du contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).  
  
### Pour ajouter un contrôle par programme  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> de la collection retournée par la propriété <xref:System.Windows.Forms.Control.Controls%2A> de <xref:System.Windows.Forms.TabPage> :  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## Voir aussi  
 [TabControl, contrôle](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [Vue d'ensemble du contrôle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [Comment : modifier l'apparence du contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)   
 [Comment : désactiver les pages d'onglets](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)