---
title: "Comment&#160;: d&#233;sactiver des ToolStripMenuItems | Microsoft Docs"
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
  - "désactiver les éléments de menu"
  - "éléments de menu, désactiver"
  - "éléments de menu, activer"
  - "menus, désactiver les éléments de menu"
  - "ToolStripMenuItems, désactiver"
  - "ToolStripMenuItems, activer"
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: d&#233;sactiver des ToolStripMenuItems
Vous pouvez limiter ou élargir le nombre de commandes qu'un utilisateur peut exécuter en activant et désactivant des éléments de menu en fonction des activités de l'utilisateur.  Les éléments de menu sont activés par défaut à leur création, mais ce paramétrage peut être ajusté par la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>.  Vous pouvez manipuler cette propriété au moment du design dans la fenêtre **Propriétés** ou par programme en la définissant dans le code.  
  
### Pour désactiver un élément de menu par programme  
  
-   Dans la méthode avec laquelle vous définissez les propriétés de l'élément de menu, ajoutez le code pour affecter à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> la valeur `false`.  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  La désactivation du premier élément ou de l'élément de menu de niveau supérieur dans un menu masque tous les éléments de menu contenus dans le menu, mais ne les désactive pas.  De même, la désactivation d'un élément de menu qui contient des éléments de sous\-menu masque les éléments de sous\-menu, mais ne les désactive pas.  Si toutes les commandes d'un menu sont indisponibles, une bonne pratique de programmation consistera à cacher et désactiver le menu tout entier pour obtenir une interface utilisateur plus nette.  Vous devez masquer et désactiver le menu, puis désactivez chaque élément de menu et élément de sous\-menu, parce que le masquage seul n'empêche pas l'accès à une commande de menu via une touche de raccourci.  Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Visible%2A> d'un élément de menu de niveau supérieur à `false` pour masquer le menu entier.  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [Comment : masquer des ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)