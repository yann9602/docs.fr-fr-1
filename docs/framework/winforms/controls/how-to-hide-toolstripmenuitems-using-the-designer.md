---
title: "Comment&#160;: masquer des ToolStripMenuItems &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "éléments de menu, masquer"
  - "MenuStrip (contrôle Windows Forms), masquer les éléments de menu dans le concepteur"
  - "ToolStripMenuItems, masquer les éléments de menu dans le concepteur"
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: masquer des ToolStripMenuItems &#224; l&#39;aide du concepteur
Le masquage des éléments de menu permet de contrôler l'interface utilisateur de votre application et de restreindre les commandes accessibles à l'utilisateur.  Il est souvent conseillé de masquer un menu quand tous ses éléments sont indisponibles.  Ainsi, l'utilisateur est moins distrait.  En outre, vous pouvez souhaiter à la fois masquer et désactiver le menu ou l'élément de menu, dans la mesure où le fait de le masquer seul n'empêche pas l'utilisateur d'accéder à une commande de menu en utilisant une touche de raccourci.  Pour plus d'informations sur la désactivation des éléments de menu, consultez [Comment : désactiver des ToolStripMenuItems à l'aide du concepteur](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour masquer un menu du niveau supérieur et ses éléments de sous\-menu  
  
1.  Sélectionnez l'élément de menu de niveau supérieur et affectez à sa propriété <xref:System.Windows.Forms.ToolStripItem.Visible%2A> ou <xref:System.Windows.Forms.ToolStripItem.Available%2A> la valeur `false`.  
  
     Lorsque vous masquez l'élément de menu de niveau supérieur, tous les éléments de menu de ce menu sont également masqués.  Si vous cliquez quelque part autre que sur le <xref:System.Windows.Forms.MenuStrip> après avoir attribué à <xref:System.Windows.Forms.ToolStripItem.Visible%2A> la valeur `false`, l'élément de menu de niveau supérieur entier et ses éléments de sous\-menu disparaissent de votre formulaire, vous montrant ainsi l'effet de votre action au moment l'exécution.  Pour afficher l'élément de menu de niveau supérieur masqué au moment du design, cliquez sur le <xref:System.Windows.Forms.MenuStrip> dans la **Barre d'état des composants**, dans la fenêtre **Structure du document** ou en haut de la grille des propriétés.  
  
> [!NOTE]
>  Vous masquerez rarement un menu entier à l'exception des menus enfants d'interface multidocument \(MDI, Multiple Document Interface\) dans un scénario de fusion.  
  
### Pour masquer un élément de sous\-menu  
  
1.  Sélectionnez l'élément de sous\-menu et attribuez à sa propriété <xref:System.Windows.Forms.ToolStripItem.Visible%2A> la valeur `false`.  
  
     Lorsque vous masquez un élément de sous\-menu, il reste visible sur votre formulaire au moment du design afin que vous puissiez le sélectionner facilement pour d'autres tâches.  Il sera en fait masqué au moment de l'exécution.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>   
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)   
 [Comment : désactiver des ToolStripMenuItems à l'aide du concepteur](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)