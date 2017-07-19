---
title: "Comment&#160;: d&#233;sactiver des ToolStripMenuItems &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "éléments de menu, désactiver"
  - "menus, désactiver les éléments"
  - "MenuStrip (contrôle Windows Forms), désactiver les éléments de menu dans le concepteur"
  - "ToolStripMenuItems, désactiver dans le concepteur"
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: d&#233;sactiver des ToolStripMenuItems &#224; l&#39;aide du concepteur
Vous pouvez limiter ou élargir le nombre de commandes qu'un utilisateur peut exécuter en activant et désactivant des éléments de menu en fonction des activités de l'utilisateur.  Les éléments de menu sont activés par défaut à leur création, mais ce paramétrage peut être ajusté par la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>.  Vous pouvez manipuler cette propriété au moment du design dans la fenêtre **Propriétés** ou par programme en la définissant dans le code.  Pour plus d'informations, consultez [Comment : désactiver des ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour désactiver un élément de menu au moment du design  
  
1.  Avec l'élément de menu sélectionné sur le formulaire, attribuez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> la valeur `false`.  
  
    > [!TIP]
    >  La désactivation du premier élément de menu ou de l'élément de menu de niveau supérieur dans un menu désactive tous les éléments de menu contenus dans le menu.  De même, si vous désactivez un élément de menu qui contient des éléments de sous\-menu, ces derniers seront également désactivés.  Si toutes les commandes d'un menu sont indisponibles, une bonne pratique de programmation consistera à cacher et désactiver le menu tout entier pour obtenir une interface utilisateur plus nette.  Vous devez à la fois masquer et désactiver le menu, car un simple masquage n'empêche pas l'accès au menu par le biais d'une touche de raccourci.  Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Visible%2A> d'un élément de menu de niveau supérieur à `false` pour masquer le menu entier.  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [Comment : masquer des ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)