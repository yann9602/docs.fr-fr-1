---
title: "Comment&#160;: ajouter et supprimer des &#233;l&#233;ments avec le contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "ListView (contrôle Windows Forms), ajouter des éléments de liste"
  - "ListView (contrôle Windows Forms), remplir"
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: ajouter et supprimer des &#233;l&#233;ments avec le contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur
Pour ajouter un élément à un contrôle <xref:System.Windows.Forms.ListView> Windows Forms, vous devez le spécifier, puis lui assigner des propriétés.  L'ajout ou la suppression d'éléments peut s'effectuer à n'importe quel moment.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.ListView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter ou supprimer des éléments à l'aide du concepteur :  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.ListView>.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur le **bouton de sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.  
  
     L'**éditeur de collections ListViewItem** s'affiche.  
  
3.  Pour ajouter un élément, cliquez sur le bouton **Ajouter**.  Vous pouvez ensuite définir les propriétés du nouvel élément, par exemple les propriétés <xref:System.Windows.Forms.ListView.Text%2A> et <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.  
  
4.  Pour supprimer un élément, sélectionnez\-le et cliquez sur le bouton **Supprimer**.  
  
## Voir aussi  
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Comment : ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [Comment : afficher des sous\-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [Comment : afficher des icônes pour le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [Comment : grouper des éléments dans un contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)