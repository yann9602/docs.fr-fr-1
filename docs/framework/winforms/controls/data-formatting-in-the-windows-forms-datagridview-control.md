---
title: "Mise en forme de données dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e716dc74946ac6f18ab82c6834518f0bd6bbea76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Mise en forme de données dans le contrôle DataGridView Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle fournit une conversion automatique entre les valeurs de cellule et les types de données que les colonnes parentes affichent. Colonnes de zone de texte, par exemple, affichent des représentations de chaîne des valeurs d’énumération, nombre, date et heure et convertissent des valeurs de chaîne d’entrée par l’utilisateur pour les types requis par le magasin de données.  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>Mise en forme avec la classe DataGridViewCellStyle  
 Le <xref:System.Windows.Forms.DataGridView> contrôle fournit des données de base de mise en forme des valeurs de cellule via la <xref:System.Windows.Forms.DataGridViewCellStyle> classe. Vous pouvez utiliser la <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriété des valeurs de format de date, heure, nombre et d’énumération pour la culture par défaut actuelle à l’aide de spécificateurs de format décrits dans [mise en forme des Types](../../../../docs/standard/base-types/formatting-types.md). Vous pouvez également mettre en forme ces valeurs pour des cultures spécifiques à l’aide de la <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A> propriété. Le format spécifié est utilisé pour afficher des données et analyser les données que l’utilisateur entre dans le format spécifié.  
  
 La <xref:System.Windows.Forms.DataGridViewCellStyle> classe fournit des propriétés de mise en forme supplémentaires pour wordwrap, l’alignement de texte et l’affichage personnalisé des valeurs null de base de données. Pour plus d’informations, consultez [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## <a name="formatting-with-the-cellformatting-event"></a>Mise en forme avec l’événement CellFormatting  
 Si la mise en forme de base ne répond pas à vos besoins, vous pouvez fournir des données personnalisées dans un gestionnaire pour la mise en forme le <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> événement. Le <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passé au gestionnaire a une <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriété qui contient la valeur de cellule à l’origine. Normalement, cette valeur est automatiquement convertie en type d’affichage. Pour convertir la valeur vous-même, attribuez le <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> propriété à une valeur de type d’affichage.  
  
> [!NOTE]
>  Si une chaîne de format est en vigueur pour la cellule, elle substitue votre modification de la <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> valeur de propriété, sauf si vous définissez la <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> propriété `true`.  
  
 Le <xref:System.Windows.Forms.DataGridView.CellFormatting> événement est également utile lorsque vous souhaitez définir <xref:System.Windows.Forms.DataGridViewCellStyle> propriétés pour les cellules individuelles en fonction de leurs valeurs. Pour plus d’informations, consultez [Comment : personnaliser la mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Si l’analyse par défaut des valeurs spécifiées par l’utilisateur ne répond pas à vos besoins, vous pouvez gérer le <xref:System.Windows.Forms.DataGridView.CellParsing> l’événement de la <xref:System.Windows.Forms.DataGridView> contrôle pour fournir l’analyse personnalisée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour mettre en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [Guide pratique pour personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
