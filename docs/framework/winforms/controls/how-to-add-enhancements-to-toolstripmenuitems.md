---
title: "Comment&#160;: ajouter des am&#233;liorations aux ToolStripMenuItems | Microsoft Docs"
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
  - "coches, ajouter aux menus"
  - "commandes (Windows Forms), regrouper sur les menus"
  - "images (Windows Forms), ajouter aux menus"
  - "raccourcis clavier, afficher dans les menus"
  - "éléments de menu, ajouter des coches"
  - "éléments de menu, ajouter des images"
  - "éléments de menu, afficher les touches d'accès"
  - "éléments de menu, afficher les touches de raccourci"
  - "éléments de menu, afficher les séparateurs"
  - "menus, regrouper les commandes"
  - "séparateurs, afficher dans les menus"
  - "ToolStripMenuItems"
  - "ToolStripMenuItems, ajouter des coches"
  - "ToolStripMenuItems, ajouter des images"
  - "ToolStripMenuItems, afficher les touches d'accès"
  - "ToolStripMenuItems, afficher les touches de raccourci"
  - "ToolStripMenuItems, afficher les barres de séparation"
  - "ToolStripSeparators, afficher sur les MenuStrips"
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: ajouter des am&#233;liorations aux ToolStripMenuItems
Vous pouvez améliorer la facilité d'utilisation des contrôles <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> des façons suivantes :  
  
-   Ajoutez des coches pour indiquer si une fonction est active ou non \(par exemple, si une règle est affichée le long de la marge d'une application de traitement de texte\) ou pour désigner le fichier d'une liste de fichiers qui se trouve affiché \(par exemple, dans le menu **Fenêtre**\).  
  
-   Ajoutez les images qui visuellement représentent des commandes de menu.  
  
-   Affichez des touches de raccourci pour fournir un clavier autre à la souris pour exécuter des commandes.  Par exemple, appuyez sur CTRL\+C exécute la commande **Copy**.  
  
-   Affichez des touches d'accès rapide pour fournir un clavier autre à la souris pour la navigation de menu.  Par exemple, appuyez sur ALT\+F pour choisir le menu **Fichier**.  
  
-   Affichez des barres de séparation pour regrouper des commandes connexes et rendre des menus plus lisibles.  
  
### Pour afficher une coche sur une commande de menu  
  
-   affectez à sa propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> la valeur `true`.  
  
     Affectez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A> la valeur `true`.  Utilisez cette procédure uniquement si vous souhaitez que la commande de menu apparaisse comme cochée par défaut, indépendamment de sa sélection ou non.  
  
### Pour afficher une coche qui modifie l'état à chaque clic  
  
-   Affectez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> du contrôle la valeur `true`.  
  
### Pour ajouter une image à une commande de menu  
  
-   Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Image%2A> de la commande de menu selon le nom de l'image.  Si la propriété <xref:System.Windows.Forms.ToolStripItemDisplayStyle> de cette commande de menu a la valeur <xref:System.Windows.Forms.ToolStripItemDisplayStyle> ou <xref:System.Windows.Forms.ToolStripItemDisplayStyle>, l'image ne peut pas être affichée.  
  
> [!NOTE]
>  La marge d'image peut également afficher une coche si vous le décidez.  Vous pouvez également attribuer à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> de l'image la valeur `true`, et l'image apparaîtra avec une bordure hachurée au moment de l'exécution.  
  
### Pour afficher une touche de raccourci pour une commande de menu  
  
-   Définissez la propriété <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A> de la commande de menu selon la séquence de touches désirée, telle que CTRL\+O pour la commande de menu **Ouvrir** et attribuez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> la valeur `true`.  
  
### Pour afficher des touches de raccourci personnalisées pour une commande de menu  
  
-   Définissez la propriété <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> de la commande de menu selon la séquence de touches désirée, telle que CTRL\+MAJ\+O plutôt que MAJ\+CTRL\+O, et attribuez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A> la valeur `true`.  
  
### Pour afficher une touche d'accès rapide pour une commande de menu  
  
-   Lorsque vous définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> pour la commande de menu, entrez une perluète \(&\) devant la lettre qui doit être soulignée comme touche d'accès rapide.  Par exemple, si vous tapez  `&Open`  comme propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> d'un élément de menu, il apparaîtra ainsi : **O**uvrir.  
  
     Pour naviguer jusqu'à cet élément de menu, appuyez sur ALT pour amener le focus sur le <xref:System.Windows.Forms.MenuStrip>, puis sur la touche d'accès rapide correspondant au nom du menu.  Lorsque le menu s'ouvre en affichant les éléments avec leurs touches d'accès rapide, il suffit d'appuyer sur l'une de ces touches pour sélectionner la commande de menu correspondant.  
  
> [!NOTE]
>  Évitez de définir des touches d'accès rapide en double, en définissant par exemple deux fois ALT\+F dans le même système de menus.  L'ordre de sélection des touches d'accès rapide en double ne peut pas être garanti.  
  
### Pour afficher une barre de séparation entre des commandes de menu  
  
-   Après avoir défini vos <xref:System.Windows.Forms.MenuStrip> et les éléments qui le composent, utilisez la méthode <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> ou <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> pour ajouter les commandes de menu et les contrôles <xref:System.Windows.Forms.ToolStripSeparator> au <xref:System.Windows.Forms.MenuStrip> dans l'ordre que vous souhaitez.  
  
     \[Visual Basic\]  
  
    ```  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
  
    ```  
  
     \[C\#\]  
  
    ```  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)