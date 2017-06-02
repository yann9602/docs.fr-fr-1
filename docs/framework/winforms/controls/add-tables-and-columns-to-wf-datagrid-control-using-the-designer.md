---
title: "Comment&#160;: ajouter des tables et des colonnes au contr&#244;le DataGrid Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "colonnes (Windows Forms), ajouter au contrôle DataGrid"
  - "DataGrid (contrôle Windows Forms), ajouter des tables et des colonnes"
  - "tables (Windows Forms), ajouter au contrôle DataGrid"
ms.assetid: 4a6d1b34-b696-476b-bf8a-57c6230aa9e1
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: ajouter des tables et des colonnes au contr&#244;le DataGrid Windows Forms &#224; l&#39;aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Vous pouvez afficher, dans des tables et des colonnes, les données du contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms en créant des objets <xref:System.Windows.Forms.DataGridTableStyle> et en les ajoutant à l'objet <xref:System.Windows.Forms.GridTableStylesCollection>, lequel est accessible par le biais de la propriété <xref:System.Windows.Forms.DataGrid.TableStyles%2A> du contrôle <xref:System.Windows.Forms.DataGrid>.  Chaque style de table affiche le contenu de toute table de données spécifiée dans la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> de <xref:System.Windows.Forms.DataGridTableStyle>.  Par défaut, un style de table sans style de colonne spécifié affiche toutes les colonnes de la table de données.  Vous pouvez limiter les colonnes de la table qui apparaissent en ajoutant des objets <xref:System.Windows.Forms.DataGridColumnStyle> à <xref:System.Windows.Forms.GridColumnStylesCollection>, lequel est accessible par le biais de la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> de chaque <xref:System.Windows.Forms.DataGridTableStyle>.  
  
 La procédure suivante nécessite un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGrid>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  Par défaut, dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils**.  Pour plus d'informations sur son ajout, consultez [How to: Add Items to the Toolbox](http://msdn.microsoft.com/fr-fr/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter une table au contrôle DataGrid dans le concepteur  
  
1.  Pour afficher des données dans la table, vous devez d'abord lier le contrôle <xref:System.Windows.Forms.DataGrid> à un groupe de données.  Pour plus d'informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une source de données à l'aide du concepteur](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md).  
  
2.  Sélectionnez la propriété <xref:System.Windows.Forms.DataGrid.TableStyles%2A> du contrôle <xref:System.Windows.Forms.DataGrid> dans la fenêtre Propriétés, puis cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété pour afficher l'**éditeur de collections DataGridTableStyle**.  
  
3.  Dans l'éditeur de collections, cliquez sur **Ajouter** pour insérer un style de table.  
  
4.  Cliquez sur **OK** pour fermer l'éditeur de collections, puis rouvrez\-le en cliquant sur le bouton de sélection situé en regard de la propriété <xref:System.Windows.Forms.DataGrid.TableStyles%2A>.  
  
     Lorsque vous rouvrez l'éditeur de collections, toutes les tables de données liées au contrôle s'affichent dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> du style de table.  
  
5.  Dans la zone **Membres** de l'éditeur de collections, cliquez sur le style de table.  
  
6.  Dans la zone **Propriétés** de l'éditeur de collections, sélectionnez la valeur <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> de la table à afficher.  
  
### Pour ajouter une table au contrôle DataGrid dans le concepteur  
  
1.  Dans la zone **Membres** de l'**éditeur de collections DataGridTableStyle**, cliquez sur le style de table approprié.  Dans la zone **Propriétés** de l'éditeur de collections, sélectionnez la collection <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>, puis cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété pour afficher l'**éditeur de collections DataGridColumnStyle**.  
  
2.  Dans l'éditeur de collections, cliquez sur **Ajouter** pour insérer un style de colonne ou cliquez sur la flèche vers le bas située en regard de **Ajouter** pour spécifier un type de colonne.  
  
     Dans la zone déroulante, vous pouvez sélectionner le type <xref:System.Windows.Forms.DataGridTextBoxColumn> ou <xref:System.Windows.Forms.DataGridBoolColumn>.  
  
3.  Cliquez sur OK pour fermer l'**éditeur de collections DataGridColumnStyle**, puis rouvrez\-le en cliquant sur le bouton de sélection situé en regard de la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>.  
  
     Lorsque vous rouvrez l'éditeur de collections, toutes les colonnes de données situées dans la table de données liée s'affichent dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> du style de colonne.  
  
4.  Dans la zone **Membres** de l'éditeur de collections, cliquez sur le style de colonne.  
  
5.  Dans la zone **Propriétés** de l'éditeur de collections, sélectionnez la valeur <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> de la colonne à afficher.  
  
## Voir aussi  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)