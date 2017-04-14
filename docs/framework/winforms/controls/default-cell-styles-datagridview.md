---
title: "Comment&#160;: d&#233;finir des styles de cellules et des formats de donn&#233;es par d&#233;faut pour le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "cellules, définir des styles"
  - "données (Windows Forms), définir des formats"
  - "formats de données"
  - "DataGridView (contrôle Windows Forms), styles de cellules"
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: d&#233;finir des styles de cellules et des formats de donn&#233;es par d&#233;faut pour le contr&#244;le DataGridView Windows Forms &#224; l&#39;aide du concepteur
Le contrôle <xref:System.Windows.Forms.DataGridView> vous permet de spécifier des styles de cellule et des formats de données de cellule pour le contrôle entier, pour des colonnes spécifiques, pour des en\-têtes de ligne et de colonne, et pour des lignes alternantes afin de créer un effet de registre.  Les styles par défaut définis pour le contrôle entier sont substitués par les styles par défaut définis pour les colonnes et les lignes alternantes.  En outre, les styles que vous définissez dans le code pour les lignes et les cellules individuelles se substituent aux styles par défaut.  
  
 Pour plus d'informations sur les styles des cellules, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  Pour définir des styles pour les lignes alternantes, consultez [Comment : définir des styles de ligne en alternance pour le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Vous pouvez également définir des styles à l'aide de la propriété <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> pour s'appliquer à toutes les lignes qui seront ajoutées au contrôle.  Pour plus d'informations sur le modèle de ligne, consultez [Comment : utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 La procédure suivante nécessite un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir des styles par défaut pour toutes les cellules du contrôle  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.DataGridView> dans le concepteur.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>.  La boîte de dialogue **Générateur CellStyle** s'affiche.  
  
3.  Définissez le style en définissant les propriétés, à l'aide du volet **Aperçu** pour confirmer vos choix.  
  
> [!NOTE]
>  Si les styles visuels sont activés, les en\-têtes de ligne et de colonne \(à l'exception de <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>\), reçoivent automatiquement un style du thème actuel, en substituant les valeurs de propriété <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>.  
>   
>  Vous pouvez définir des styles de cellules pour plusieurs contrôles sélectionnés <xref:System.Windows.Forms.DataGridView> en utilisant le concepteur, mais uniquement s'ils ont des valeurs identiques pour la propriété du style de la cellule que vous souhaitez modifier.  Si les styles de cellules diffèrent pour cette propriété, les fenêtres **Propriétés** de la boîte de dialogue **Générateur CellStyle** seront vierges.  
  
### Pour définir des styles par défaut pour les cellules dans les colonnes individuelles  
  
1.  Cliquez avec le bouton droit sur le contrôle <xref:System.Windows.Forms.DataGridView> dans le concepteur et choisissez **Modifier les colonnes**.  
  
2.  Sélectionnez une colonne dans la liste **Colonnes sélectionnées**.  
  
3.  Dans la grille **Propriétés des colonnes**, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>.  La boîte de dialogue **Générateur CellStyle** s'affiche.  
  
4.  Définissez le style en définissant les propriétés, à l'aide du volet **Aperçu** pour confirmer vos choix.  
  
### Pour mettre en forme des données dans les cellules  
  
1.  Utilisez l'une des procédures précédentes pour afficher une boîte de dialogue **Générateur CellStyle** en rapport avec une propriété du style de la cellule par défaut.  
  
2.  Dans la boîte de dialogue **Générateur CellStyle**, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>.  Vous voyez s'afficher la boîte de dialogue **Chaîne de format**.  
  
3.  Sélectionnez un type de format, puis modifiez les détails de type \(tels que le nombre de décimales à afficher\), à l'aide de la zone **Exemple** pour confirmer vos choix.  
  
4.  Si vous liez le contrôle <xref:System.Windows.Forms.DataGridView> à une source de données qui a de fortes chances de contenir des valeurs Null, remplissez la zone de texte **Valeur null**.  Cette valeur est affichée lorsque la valeur de la cellule est égale à une référence nulle \(`Nothing` en Visual Basic\) ou <xref:System.DBNull.Value?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=fullName>   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Comment : définir des styles de ligne en alternance pour le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)   
 [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa)   
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)