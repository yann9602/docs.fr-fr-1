---
title: "Mise en forme de donn&#233;es dans le contr&#244;le DataGridView Windows&#160;Forms | Microsoft Docs"
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
  - "données (Windows Forms), mettre en forme dans les grilles"
  - "grilles de données, mettre en forme des données"
  - "DataGridView (contrôle Windows Forms), mettre en forme des données"
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Mise en forme de donn&#233;es dans le contr&#244;le DataGridView Windows&#160;Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> assure la conversion automatique entre les valeurs de cellules et les types de données que les colonnes parentes affichent.  Par exemple, les colonnes de zone de texte affichent des représentations sous forme de chaîne pour les valeurs de date, d'heure, de nombre et d'énumération, et convertissent les valeurs de chaîne entrées par utilisateur en les types requis par le magasin de données.  
  
## Mise en forme avec la classe DataGridViewCellStyle  
 Le contrôle <xref:System.Windows.Forms.DataGridView> fournit des données de base qui mettent en forme les valeurs des cellules par le biais de la classe <xref:System.Windows.Forms.DataGridViewCellStyle>.  Vous pouvez utiliser la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> pour mettre en forme les valeurs de date, d'heure, de nombre et d'énumération pour la culture par défaut actuelle à l'aide des spécificateurs de format décrits dans [Mise en forme des types](../../../../docs/standard/base-types/formatting-types.md).  Vous pouvez également mettre en forme ces valeurs pour des cultures spécifiques qui utilisent la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>.  Le format spécifié est utilisé à la fois pour afficher des données et analyser les données que l'utilisateur entre dans le format spécifié.  
  
 La classe <xref:System.Windows.Forms.DataGridViewCellStyle> fournit des propriétés de mise en forme supplémentaires pour le retour automatique à la ligne, l'alignement de texte et l'affichage personnalisé des valeurs de base de données nulles.  Pour plus d'informations, consultez [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
## Mise en forme avec l'événement CellFormatting  
 Si la mise en forme de base ne répond pas à vos besoins, vous pouvez fournir une mise en forme de données personnalisée dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName>.  Le <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> passé au gestionnaire a une propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> qui contient initialement la valeur de la cellule.  Normalement, cette valeur est convertie automatiquement en type d'affichage.  Pour convertir la valeur vous\-même, attribuez à la propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> une valeur du type d'affichage.  
  
> [!NOTE]
>  Si une chaîne de mise en forme est appliquée à la cellule, elle substitue votre modification de la valeur de propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> à moins que vous ne donniez à la propriété <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A> la valeur `true`.  
  
 L'événement <xref:System.Windows.Forms.DataGridView.CellFormatting> est également utile lorsque vous souhaitez définir des propriétés <xref:System.Windows.Forms.DataGridViewCellStyle> pour des cellules individuelles en fonction de leurs valeurs.  Pour plus d'informations, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
 Si l'analyse par défaut des valeurs spécifiées par utilisateur ne répond pas à vos besoins, vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.CellParsing> du contrôle <xref:System.Windows.Forms.DataGridView> pour fournir l'analyse personnalisée.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)