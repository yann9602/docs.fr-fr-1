---
title: "Comment&#160;: ajouter des colonnes au contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "colonnes (Windows Forms), ajouter à des contrôles ListView"
  - "ListView (contrôle Windows Forms), ajouter des en-têtes de colonnes"
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: ajouter des colonnes au contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur
Le contrôle Windows Forms <xref:System.Windows.Forms.ListView> peut afficher plusieurs colonnes pour chaque élément de la liste dans la vue **Détails**.  Vous pouvez utiliser les colonnes pour afficher plusieurs types d'informations concernant l'élément de liste.  Par exemple, une liste de fichiers peut afficher le nom d'un fichier, son type, sa taille et la date de sa dernière modification.  Pour plus d'informations sur le remplissage des colonnes une fois qu'elles sont créées, consultez [Comment : afficher des sous\-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.ListView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter des colonnes dans le concepteur  
  
1.  Dans la fenêtre **Propriétés**, affectez <xref:System.Windows.Forms.View> à la propriété <xref:System.Windows.Forms.ListView.View%2A> du contrôle.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur le **bouton de sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.ListView.Columns%2A>.  
  
     L'**éditeur de collections ColumnHeader** s'affiche.  
  
3.  Ajoutez des colonnes en vous servant du bouton **Ajouter**.  Vous pouvez ensuite sélectionner l'en\-tête de colonne et définir son texte \(sa légende\), l'alignement de son texte et sa largeur.  
  
## Voir aussi  
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [Comment : afficher des sous\-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [Comment : afficher des icônes pour le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)