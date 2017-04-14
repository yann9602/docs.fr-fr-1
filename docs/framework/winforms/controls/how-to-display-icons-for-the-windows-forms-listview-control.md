---
title: "Comment&#160;: afficher des ic&#244;nes pour le contr&#244;le ListView Windows Forms | Microsoft Docs"
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
  - "icônes, afficher les contrôles ListView"
  - "ImageList (composant Windows Forms), avec un contrôle ListView"
  - "Liste (vues), afficher les icônes"
  - "listes, afficher les icônes"
  - "ListView (contrôle Windows Forms), afficher les icônes"
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: afficher des ic&#244;nes pour le contr&#244;le ListView Windows Forms
Le contrôle <xref:System.Windows.Forms.ListView> Windows Forms peut afficher des icônes à partir de trois listes d'images.  Les vues List, Details et SmallIcon affichent des images de la liste d'images spécifiée par la propriété <xref:System.Windows.Forms.ListView.SmallImageList%2A>.  La vue LargeIcon affiche des images de la liste d'images spécifiée par la propriété <xref:System.Windows.Forms.ListView.LargeImageList%2A>.  La vue Liste peut également afficher, en regard des grandes ou des petites icônes, un ensemble d'icônes supplémentaire défini dans la propriété <xref:System.Windows.Forms.ListView.StateImageList%2A>.  Pour plus d'informations sur les listes d'images, consultez [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) et [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
### Pour afficher des images dans une vue Liste  
  
1.  Affectez à la propriété appropriée \(<xref:System.Windows.Forms.ListView.SmallImageList%2A>, <xref:System.Windows.Forms.ListView.LargeImageList%2A> ou <xref:System.Windows.Forms.ListView.StateImageList%2A>\) le composant <xref:System.Windows.Forms.ImageList> existant que vous souhaitez utiliser.  
  
     Ces propriétés peuvent être définies dans le concepteur à l'aide de la fenêtre Propriétés ou dans le code.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  Définissez la propriété <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> ou <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> de chaque élément de la liste à laquelle est associée une icône.  
  
     Ces propriétés peuvent être définies dans le code ou dans l'**Éditeur de collections ListViewItem**.  Pour afficher l'**Éditeur de collections ListViewItem**, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) en regard de la propriété <xref:System.Windows.Forms.ListView.Items%2A> dans la fenêtre **Propriétés**.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## Voir aussi  
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [Comment : ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)