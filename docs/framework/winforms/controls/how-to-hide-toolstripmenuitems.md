---
title: "Comment&#160;: masquer des ToolStripMenuItems | Microsoft Docs"
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
  - "masquer les éléments de menu"
  - "éléments de menu, masquer"
  - "menus, masquer les éléments de menu"
  - "MenuStrip (contrôle Windows Forms), masquer les éléments de menu"
  - "ToolStripMenuItems, masquer"
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: masquer des ToolStripMenuItems
Le masquage des éléments de menu permet de contrôler l'interface utilisateur de votre application et de restreindre les commandes accessibles à l'utilisateur.  Il est souvent conseillé de masquer un menu quand tous ses éléments sont indisponibles.  Ainsi, l'utilisateur est moins distrait.  En outre, vous pouvez souhaiter à la fois masquer et désactiver le menu ou l'élément de menu, dans la mesure où le fait de le masquer seul n'empêche pas l'utilisateur d'accéder à une commande de menu en utilisant une touche de raccourci.  
  
### Pour masquer un élément de menu par programme  
  
-   Dans la méthode où vous définissez les propriétés de l'élément de menu, ajoutez le code pour attribuer à la propriété <xref:System.Windows.Forms.ToolStripItem.Visible%2A> la valeur `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>   
 <xref:System.Windows.Forms.MenuStrip>   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)   
 [Comment : désactiver des ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md)