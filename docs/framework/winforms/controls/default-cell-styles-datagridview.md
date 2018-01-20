---
title: "Comment : définir des styles de cellules et des formats de données par défaut pour le contrôle DataGridView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 65f876742526d13093a852e99f4e6a069c3fba47
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>Comment : définir des styles de cellules et des formats de données par défaut pour le contrôle DataGridView Windows Forms à l'aide du concepteur
Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de spécifier des styles de cellules par défaut et de formats de données pour l’ensemble du contrôle, pour des colonnes spécifiques, pour les en-têtes de lignes et de colonnes et de lignes pour créer un effet de livre comptable de remplacement de la cellule. Les styles par défaut définie pour l’ensemble du contrôle sont remplacés par les styles par défaut définis pour les colonnes et lignes en alternance. En outre, les styles que vous définissez dans le code pour des lignes individuelles et les cellules remplacent les styles par défaut.  
  
 Pour plus d’informations sur les styles de cellules, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md). Pour définir des styles pour les lignes en alternance, consultez [Comment : définir des Styles de ligne en alternance pour les Windows Forms DataGridView contrôle à l’aide du concepteur](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md).  
  
 Vous pouvez également définir des styles à l’aide de la <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriété affecte toutes les lignes qui seront ajoutés au contrôle. Pour plus d’informations sur le modèle de ligne, consultez [Comment : utiliser le modèle de ligne pour personnaliser les lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md).  
  
 Les procédures suivantes requièrent une **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>Pour définir les styles par défaut pour toutes les cellules dans le contrôle  
  
1.  Sélectionnez le <xref:System.Windows.Forms.DataGridView> contrôle dans le concepteur.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté du <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> propriété. Le **Générateur CellStyle** boîte de dialogue s’affiche.  
  
3.  Définir le style en définissant les propriétés, à l’aide de la **aperçu** volet pour confirmer votre choix.  
  
> [!NOTE]
>  Si les styles visuels sont activés, les en-têtes de ligne et de colonne (à l’exception de la <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) reçoivent automatiquement un style du thème actuel, remplaçant la <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A> les valeurs de propriété.  
>   
>  Vous pouvez définir des styles de cellules pour plusieurs sélectionné <xref:System.Windows.Forms.DataGridView> contrôle à l’aide du concepteur, mais uniquement si elles ont des valeurs identiques pour la propriété de style de cellule à modifier. Si les styles de cellules diffèrent pour cette propriété, le **propriétés** windows de le **Générateur CellStyle** boîte de dialogue est vide.  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>Pour définir les styles par défaut pour les cellules dans les colonnes individuelles  
  
1.  Cliquez sur le <xref:System.Windows.Forms.DataGridView> contrôler dans le concepteur et choisissez **modifier les colonnes**.  
  
2.  Sélectionnez une colonne dans la **colonnes sélectionnées** liste.  
  
3.  Dans le **propriétés de la colonne** grille, cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté du <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriété. Le **Générateur CellStyle** boîte de dialogue s’affiche.  
  
4.  Définir le style en définissant les propriétés, à l’aide de la **aperçu** volet pour confirmer votre choix.  
  
### <a name="to-format-data-in-cells"></a>Pour mettre en forme les données des cellules  
  
1.  Utilisez une des procédures précédentes pour afficher une **Générateur CellStyle** boîte de dialogue relatives à une propriété de style de cellule par défaut.  
  
2.  Dans le **Générateur CellStyle** boîte de dialogue, cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté du <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriété. Le **chaîne de Format** boîte de dialogue s’affiche.  
  
3.  Sélectionnez un type de format, puis modifiez les détails du type (par exemple, le nombre de décimales à afficher), à l’aide de la **exemple** à cocher pour confirmer votre choix.  
  
4.  Si vous liez le <xref:System.Windows.Forms.DataGridView> contrôle à une source de données qui est susceptible de contenir des valeurs null, renseignez le **valeur Null** zone de texte. Cette valeur est affichée lorsque la valeur de cellule est égale à une référence null (`Nothing` en Visual Basic) ou <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>  
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour définir des styles de ligne en alternance pour le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/set-alternating-row-styles-for-the-datagrid-using-the-designer.md)  
 [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
