---
title: "Comment&#160;: d&#233;placer des ToolStripMenuItems | Microsoft Docs"
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
  - "éléments de menu, couper-coller"
  - "éléments de menu, glisser-déplacer"
  - "éléments de menu, déplacer"
  - "menus, réorganiser les éléments"
  - "MenuStrip (contrôle Windows Forms), réorganiser les éléments"
  - "ToolStripMenuItems, couper-coller"
  - "ToolStripMenuItems, glisser-déplacer"
  - "ToolStripMenuItems, déplacer"
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: d&#233;placer des ToolStripMenuItems
Au moment du design, vous pouvez copier l'intégralité des menus du niveau supérieur et leurs éléments de menu vers un autre emplacement sur le <xref:System.Windows.Forms.MenuStrip>.  Vous pouvez également déplacer des éléments de menu individuels entre des menus du niveau supérieur ou modifier la position d'éléments de menu dans un menu.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour déplacer un menu du niveau supérieur et ses éléments de menu vers un autre emplacement de niveau supérieur  
  
1.  Cliquez et maintenez le bouton gauche de la souris enfoncé dans le menu que vous souhaitez déplacer.  
  
2.  Faites glisser le point d'insertion jusqu'au menu de niveau supérieur qui se trouve devant le nouvel emplacement prévu, puis relâchez le bouton gauche de la souris.  
  
     Le menu sélectionné se déplace à droite du point d'insertion.  
  
### Pour déplacer un menu de niveau supérieur et ses éléments de menu vers un emplacement déroulant  
  
1.  Cliquez sur le menu que vous souhaitez déplacer et appuyez sur CTRL\+X, ou cliquez avec le bouton droit sur le menu et sélectionnez **Couper** dans le menu contextuel.  
  
2.  Dans le menu de niveau supérieur de destination, cliquez sur l'élément de menu au\-dessus du nouvel emplacement prévu et appuyez sur CTRL\+V, ou cliquez avec le bouton droit sur l'élément de menu au\-dessus du nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.  
  
     Le menu que vous venez de couper est inséré après l'élément de menu sélectionné.  
  
### Pour déplacer un élément de menu dans un menu à l'aide de l'éditeur de collections Items  
  
1.  Cliquez avec le bouton droit sur le menu qui contient l'élément de menu que vous souhaitez déplacer.  
  
2.  Dans le menu contextuel, choisissez **Modifier les DropDownItems**.  
  
3.  Dans l'**éditeur de collections Items**, cliquez sur l'élément de menu que vous souhaitez déplacer.  
  
4.  Cliquez sur les touches Flèche bas et Flèche haut pour déplacer l'élément de menu dans le menu.  
  
5.  Cliquez sur **OK**.  
  
### Pour déplacer un élément de menu dans un menu à l'aide du clavier  
  
1.  Appuyez et maintenez la touche ALT enfoncée.  
  
2.  Cliquez et maintenez le bouton gauche de la souris enfoncé sur l'élément de menu que vous souhaitez déplacer.  
  
3.  Faites glisser l'élément de menu vers le nouvel emplacement, puis relâchez le bouton gauche de la souris.  
  
### Pour déplacer un élément de menu vers un autre menu  
  
1.  Cliquez sur l'élément de menu que vous souhaitez déplacer et appuyez sur CTRL\+X, ou cliquez avec le bouton droit sur l'élément de menu et sélectionnez **Couper** dans le menu contextuel.  
  
2.  Cliquez sur le menu qui contiendra l'élément de menu que vous coupez.  
  
3.  Cliquez sur l'élément de menu qui se trouve devant le nouvel emplacement prévu et appuyez sur CTRL\+V, ou cliquez avec le bouton droit sur l'élément de menu qui est situé devant le nouvel emplacement prévu et sélectionnez **Coller** dans le menu contextuel.  
  
     L'élément de menu que vous venez de couper est inséré après l'élément de menu sélectionné.  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)