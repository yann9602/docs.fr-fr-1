---
title: "Comment&#160;: cr&#233;er un formulaire MDI avec la fusion de menus et des contr&#244;les ToolStrip | Microsoft Docs"
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
  - "MenuStrip (contrôle Windows Forms)"
  - "barres d'outils (Windows Forms)"
  - "ToolStrip (contrôle Windows Forms)"
  - "ToolStripPanel (contrôle Windows Forms)"
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: cr&#233;er un formulaire MDI avec la fusion de menus et des contr&#244;les ToolStrip
L'espace de noms <xref:System.Windows.Forms?displayProperty=fullName> prend en charge plusieurs applications MDI \(Multiple Document Interface\) et le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge la fusion de menus.  Les formulaires MDI peuvent également contenir des contrôles <xref:System.Windows.Forms.ToolStrip>.  
  
 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] propose une prise en charge étendue pour cette fonctionnalité.  
  
 Consultez également [Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](http://msdn.microsoft.com/library/ms233676%20\(v=vs.110\)).  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser des contrôles <xref:System.Windows.Forms.ToolStripPanel> avec un formulaire MDI.  Le formulaire prend également en charge la fusion de menus avec les menus enfants.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## Compilation du code  
 Cet exemple de code nécessite :  
  
-   Références aux assemblys System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 [ToolStrip, contrôle](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)