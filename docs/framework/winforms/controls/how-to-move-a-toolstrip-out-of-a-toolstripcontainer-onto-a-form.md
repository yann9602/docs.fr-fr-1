---
title: "Comment&#160;: d&#233;placer un ToolStrip hors d&#39;un ToolStripContainer dans un formulaire | Microsoft Docs"
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
  - "ToolStrip (contrôle Windows Forms), apparenter aux formulaires"
  - "Windows Forms, apparenter les contrôles ToolStrip"
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;placer un ToolStrip hors d&#39;un ToolStripContainer dans un formulaire
Utilisez la procédure suivante pour déplacer un <xref:System.Windows.Forms.ToolStrip> hors d'un <xref:System.Windows.Forms.ToolStripContainer> dans un formulaire.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour déplacer un ToolStrip hors d'un ToolStripContainer dans un formulaire  
  
1.  Sélectionnez la <xref:System.Windows.Forms.ToolStrip>.  
  
2.  Coupez le <xref:System.Windows.Forms.ToolStrip> en appuyant sur CTRL\+X ou cliquez avec le bouton droit sur le <xref:System.Windows.Forms.ToolStrip> et choisissez **Couper** dans le menu contextuel.  
  
3.  Sélectionnez le formulaire.  
  
4.  Collez le <xref:System.Windows.Forms.ToolStrip> en appuyant sur CTRL\+V ou choisissez **Coller** dans le menu **Edition**.  
  
5.  Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.Dock%2A> de <xref:System.Windows.Forms.ToolStrip> la valeur **Top**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripContainer>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)