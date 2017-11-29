---
title: "Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 49d5172b2638a7ac3a6a7bf005932ba4b3f9aba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a>Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms
Les procédures suivantes montrent une mise en forme des valeurs de cellule à l’aide de la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriété d’un <xref:System.Windows.Forms.DataGridView> contrôle et de colonnes spécifiques dans un contrôle. Pour plus d’informations sur la mise en forme de données avancés, consultez [Comment : personnaliser la mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-format-currency-and-date-values"></a>Format de devise et de valeurs de date  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>. L’exemple de code suivant définit le format des colonnes spécifiques à l’aide de la <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriété des colonnes. Les valeurs dans les `UnitPrice` colonne apparaissent dans le format monétaire spécifique à la culture actuelle, les valeurs négatives entourés parenthèses. Les valeurs dans les `ShipDate` colonne s’affichent dans le format de date courte de spécifiques à la culture actuelle. Pour plus d’informations sur <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> valeurs, consultez [mise en forme des Types](../../../../docs/standard/base-types/formatting-types.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a>Pour personnaliser l’affichage des valeurs de la base de données null  
  
-   Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>. Le code suivant exemple utilise le <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriété à n’afficher « aucune entrée » dans toutes les cellules contenant les valeurs sont égales à <xref:System.DBNull.Value?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a>Pour activer wordwrap dans les cellules de texte  
  
-   Définir le <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> propriété d’un <xref:System.Windows.Forms.DataGridViewCellStyle> à un de la <xref:System.Windows.Forms.DataGridViewTriState> valeurs d’énumération. Le code suivant exemple utilise le <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriété à définir le mode habillage pour l’ensemble du contrôle.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a>Pour spécifier l’alignement du texte des cellules DataGridView  
  
-   Définir le <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> propriété d’un <xref:System.Windows.Forms.DataGridViewCellStyle> à un de la <xref:System.Windows.Forms.DataGridViewContentAlignment> valeurs d’énumération. L’exemple de code suivant définit l’alignement pour une colonne spécifique à l’aide de la <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriété de la colonne.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ces exemples nécessitent :  
  
-   A <xref:System.Windows.Forms.DataGridView> contrôle nommé `dataGridView1` qui contient une colonne nommée `UnitPrice`, une colonne nommée `ShipDate`et une colonne nommée `CustomerName`.  
  
-   des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Pour une évolutivité maximale, vous devez partager <xref:System.Windows.Forms.DataGridViewCellStyle> objets à travers plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que de définir les propriétés de style pour chaque élément séparément. Pour plus d’informations, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 [Mise en forme des types](../../../../docs/standard/base-types/formatting-types.md)
