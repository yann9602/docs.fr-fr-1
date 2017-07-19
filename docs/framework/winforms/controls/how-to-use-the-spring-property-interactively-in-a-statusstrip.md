---
title: "Comment&#160;: utiliser la propri&#233;t&#233; Spring dans un StatusStrip de mani&#232;re interactive | Microsoft Docs"
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
  - "Spring (propriété Windows Forms)"
  - "barres d'état, exemples"
  - "StatusStrip (contrôle Windows Forms)"
  - "ToolStrip (contrôle Windows Forms)"
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: utiliser la propri&#233;t&#233; Spring dans un StatusStrip de mani&#232;re interactive
Vous pouvez utiliser la propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> pour positionner un contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> dans un contrôle <xref:System.Windows.Forms.StatusStrip>.  La propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> détermine si le contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> remplit automatiquement l'espace disponible sur le contrôle <xref:System.Windows.Forms.StatusStrip>.  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser la propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> pour positionner un contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> dans un contrôle <xref:System.Windows.Forms.StatusStrip>.  Le gestionnaire d'événements <xref:System.Windows.Forms.ToolStripItem.Click> exécute une opération « ou exclusif » \(XOR\) pour faire basculer la valeur de la propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
 Pour utiliser cet exemple de code, compilez et exécutez l'application, puis cliquez sur **Middle \(Spring\)** sur le contrôle <xref:System.Windows.Forms.StatusStrip> pour faire basculer la valeur de la propriété <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System.Design, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [ToolStrip, contrôle](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)