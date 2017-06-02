---
title: "Comment&#160;: ajouter et supprimer des &#233;l&#233;ments de menu avec le composant ContextMenu Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "menus contextuels, ajouter des éléments"
  - "menus contextuels, exemples"
  - "menus contextuels, supprimer des éléments"
  - "ContextMenu (composant Windows Forms), ajouter des éléments"
  - "ContextMenu (composant Windows Forms), supprimer des éléments"
  - "exemples (Windows Forms), menus contextuels"
  - "menus contextuels, ajouter des éléments"
  - "menus contextuels, exemples"
  - "menus contextuels, supprimer des éléments"
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: ajouter et supprimer des &#233;l&#233;ments de menu avec le composant ContextMenu Windows Forms
Explique comment ajouter et supprimer des éléments du menu contextuel dans Windows Forms.  
  
 Le composant <xref:System.Windows.Forms.ContextMenu> Windows Forms fournit un menu réunissant les commandes les plus fréquemment utilisées qui s'appliquent à l'objet sélectionné.  Vous pouvez ajouter des éléments au menu contextuel en ajoutant les objets <xref:System.Windows.Forms.MenuItem> à la collection <xref:System.Windows.Forms.Menu.MenuItems%2A>.  
  
 Vous pouvez supprimer définitivement des éléments d'un menu contextuel ; toutefois, au moment de l'exécution, il peut être plus approprié de masquer ou désactiver les éléments.  
  
> [!IMPORTANT]
>  Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent les contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes et leur ajoutent des fonctionnalités, <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
### Pour supprimer des éléments d'un menu contextuel  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> ou <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> de la collection <xref:System.Windows.Forms.Menu.MenuItems%2A> du composant <xref:System.Windows.Forms.ContextMenu> pour supprimer un élément de menu particulier.  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     ou  
  
2.  Utilisez la méthode `Clear` de la collection `MenuItems` du composant <xref:System.Windows.Forms.ContextMenu> pour supprimer tous les éléments du menu.  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ContextMenu>   
 [ContextMenu, composant](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)   
 [Vue d'ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)