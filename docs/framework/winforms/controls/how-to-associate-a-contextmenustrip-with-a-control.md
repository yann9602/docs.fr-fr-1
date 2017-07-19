---
title: "Comment&#160;: associer un ContextMenuStrip &#224; un contr&#244;le | Microsoft Docs"
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
  - "menus contextuels, associer à des contrôles"
  - "menus contextuels, associer"
  - "ContextMenuStrips, associer à des contrôles"
  - "ContextMenuStrips, associer"
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: associer un ContextMenuStrip &#224; un contr&#244;le
Après avoir créé vos contrôles et menus contextuels, appliquez les procédures suivantes pour afficher un menu contextuel donné quand l'utilisateur clique avec le bouton droit sur le contrôle.  Ces procédures associent un <xref:System.Windows.Forms.ContextMenuStrip> à un Windows Form et à un contrôle <xref:System.Windows.Forms.ToolStrip>.  
  
### Pour associer un ContextMenuStrip à un Windows Form  
  
1.  Affectez le nom du <xref:System.Windows.Forms.ContextMenuStrip> associé comme valeur de la propriété <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>.  
  
### Pour associer un ContextMenuStrip à un contrôle ToolStrip  
  
1.  Affectez le nom du <xref:System.Windows.Forms.ContextMenuStrip> associé comme valeur de la propriété <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> du contrôle.  
  
## Exemple  
 L'exemple de code suivant crée un Windows Form et un <xref:System.Windows.Forms.ToolStrip>, et associe un contrôle <xref:System.Windows.Forms.ContextMenuStrip> différent à chacun d'eux.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Data, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>   
 <xref:System.Windows.Forms.ToolStrip>   
 [Comment : ajouter des éléments de menu à un ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)   
 [ContextMenuStrip, contrôle](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)