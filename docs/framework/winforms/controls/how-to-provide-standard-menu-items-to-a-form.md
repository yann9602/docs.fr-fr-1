---
title: "Comment&#160;: fournir des &#233;l&#233;ments de menu standard &#224; un formulaire | Microsoft Docs"
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
  - "éléments de menu, standard"
  - "barres d'outils (Windows Forms)"
  - "ToolStrip (contrôle Windows Forms)"
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: fournir des &#233;l&#233;ments de menu standard &#224; un formulaire
Vous pouvez fournir un menu standard pour vos formulaires avec le contrôle <xref:System.Windows.Forms.MenuStrip>.  
  
 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] propose une prise en charge étendue pour cette fonctionnalité.  
  
 Consultez également [Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire](http://msdn.microsoft.com/library/ms233662%20\(v=vs.110\)).  
  
## Exemple  
 L'exemple de code suivant montre comment utiliser un contrôle <xref:System.Windows.Forms.MenuStrip> pour créer un formulaire avec un menu standard.  Les sélections d'élément de menu sont affichées dans un contrôle <xref:System.Windows.Forms.StatusStrip>.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)