---
title: "Modes de tri des colonnes du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, modes de tri"
  - "DataGridView (contrôle Windows Forms), mode de tri"
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Modes de tri des colonnes du contr&#244;le DataGridView Windows Forms
Les colonnes <xref:System.Windows.Forms.DataGridView> ont trois modes de tri.  Le mode de tri de chaque colonne est spécifié via la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de la colonne, qui peut être définie selon l'une des valeurs d'énumération <xref:System.Windows.Forms.DataGridViewColumnSortMode> suivantes.  
  
|Valeur de `DataGridViewColumnSortMode`|Description|  
|--------------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|Valeur par défaut pour les colonnes de zone de texte.  À moins que les en\-têtes de colonne ne soient utilisés pour la sélection, il suffit de cliquer sur l'en\-tête de colonne pour trier automatiquement le <xref:System.Windows.Forms.DataGridView> par cette colonne et afficher un glyphe qui indique l'ordre de tri.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|Valeur par défaut pour les colonnes autres que de zone de texte.  Vous pouvez trier cette colonne par programme ; toutefois, comme elle n'est pas destinée à être triée, aucun espace n'est réservé pour le glyphe de tri.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode>|Vous pouvez trier cette colonne par programme, et l'espace est réservé pour le glyphe de tri.|  
  
 Vous pouvez souhaiter modifier le mode de tri pour une colonne qui devient pat défaut <xref:System.Windows.Forms.DataGridViewColumnSortMode> si elle contient des valeurs qui peuvent être triées de manière significative.  Par exemple, si vous avez une colonne de base de données qui contient des nombres qui représentent des états d'éléments, vous pouvez afficher ces nombres comme icônes correspondantes en liant une colonne d'image à la colonne de base de données.  Vous pouvez transformer ensuite les valeurs de cellules numériques en valeurs d'affichage d'image dans un gestionnaire d'événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName>.  Dans ce cas, le fait d'attribuer à la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewColumnSortMode> permettra à vos utilisateurs de trier la colonne.  Le tri automatique permettra à vos utilisateurs de regrouper des éléments qui ont le même état si les états correspondant aux nombres n'ont pas une séquence naturelle.  Les colonnes de case à cocher sont un autre exemple où le tri automatique est utile pour regrouper des éléments dans le même état.  
  
 Vous pouvez trier un <xref:System.Windows.Forms.DataGridView> par programme, selon les valeurs d'une colonne ou de plusieurs colonnes, indépendamment des paramètres <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>.  Le tri par programme est utile lorsque vous souhaitez fournir votre propre interface utilisateur pour le tri ou lorsque vous souhaitez implémenter le tri personnalisé.  Le fait de fournir votre propre interface utilisateur de tri est utile, par exemple, lorsque vous définissez le mode de sélection <xref:System.Windows.Forms.DataGridView> de façon à activer la sélection d'en\-tête de colonne.  Dans ce cas, bien que les en\-têtes de colonne ne puissent pas être utilisés pour le tri, vous pouvez souhaiter encore que les en\-têtes affichent le glyphe de tri approprié, afin que vous puissiez attribuer à la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> la valeur <xref:System.Windows.Forms.DataGridViewColumnSortMode>.  
  
 Les colonnes définies selon le mode de tri par programme n'affichent pas automatiquement de glyphe de tri.  Pour ces colonnes, vous devez afficher le glyphe vous\-même en définissant la propriété <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName>.  Ceci est nécessaire si vous souhaitez de la souplesse dans le tri personnalisé.  Par exemple, si vous triez le <xref:System.Windows.Forms.DataGridView> par plusieurs colonnes, vous pouvez souhaiter afficher plusieurs glyphes de tri ou aucun glyphe de tri.  
  
 Bien que vous puissiez trier par programme un <xref:System.Windows.Forms.DataGridView> selon n'importe quelle colonne, certaines colonnes, comme les colonnes de bouton, peuvent ne pas contenir des valeurs susceptibles d'être triées de manière significative.  Pour ces colonnes, une propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ayant la valeur <xref:System.Windows.Forms.DataGridViewColumnSortMode> indique qu'elle ne sera jamais utilisée pour le tri, et qu'il n'est donc pas nécessaire de réserver l'espace dans l'en\-tête pour le glyphe de tri.  
  
 Lorsqu'une <xref:System.Windows.Forms.DataGridView> est triée, vous pouvez déterminer à la fois la colonne de tri et l'ordre de tri en sélectionnant les valeurs des propriétés <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> et <xref:System.Windows.Forms.DataGridView.SortOrder%2A>.  Ces valeurs ne sont pas explicites après une opération de tri personnalisée.  Pour plus d'informations sur le tri personnalisé, consultez la section Tri personnalisé plus loin dans cette rubrique.  
  
 Lorsqu'un contrôle <xref:System.Windows.Forms.DataGridView> qui contient des colonnes dépendantes et indépendantes est trié, les valeurs des colonnes indépendantes ne peuvent pas être maintenues automatiquement.  Pour maintenir ces valeurs, vous devez implémenter le mode virtuel en attribuant à la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur `true` et en gérant les événements <xref:System.Windows.Forms.DataGridView.CellValueNeeded> et <xref:System.Windows.Forms.DataGridView.CellValuePushed>.  Pour plus d'informations, consultez [Comment : implémenter le mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  Le tri par colonnes indépendantes en mode dépendant n'est pas pris en charge.  
  
## Tri par programme  
 Vous pouvez trier un <xref:System.Windows.Forms.DataGridView> par programme en appelant sa méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>.  
  
 La surcharge `Sort(DataGridViewColumn,ListSortDirection)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> prend un <xref:System.Windows.Forms.DataGridViewColumn> et une valeur d'énumération <xref:System.ComponentModel.ListSortDirection> comme paramètres.  Cette surcharge est utile lorsque vous voulez effectuer un tri par colonnes avec des valeurs qui peuvent être classées significativement, mais que vous ne souhaitez pas procéder à une configuration pour tri automatique.  Lorsque vous appelez cette surcharge et passez dans une colonne avec une valeur de propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> de <xref:System.Windows.Forms.DataGridViewColumnSortMode?displayProperty=fullName>, les propriétés <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> et <xref:System.Windows.Forms.DataGridView.SortOrder%2A> sont définies automatiquement et le glyphe de tri approprié apparaît dans l'en\-tête de colonne.  
  
> [!NOTE]
>  Lorsque le contrôle <xref:System.Windows.Forms.DataGridView> est lié à une source de données externe en définissant la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>, la surcharge de méthode `Sort(DataGridViewColumn,ListSortDirection)` ne fonctionne pas pour les colonnes indépendantes.  De plus, lorsque la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `true`, vous pouvez appeler cette surcharge uniquement pour les colonnes dépendantes.  Pour déterminer si une colonne est liée aux données, sélectionnez la valeur de propriété <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>.  Le tri de colonnes indépendantes en mode dépendant n'est pas pris en charge.  
  
## Tri personnalisé  
 Vous pouvez personnaliser <xref:System.Windows.Forms.DataGridView> en utilisant la surcharge `Sort(IComparer)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A> ou en gérant l'événement <xref:System.Windows.Forms.DataGridView.SortCompare>.  
  
 La surcharge de méthode `Sort(IComparer)` prend une instance d'une classe qui implémente l'interface <xref:System.Collections.IComparer> comme un paramètre.  Cette surcharge est utile lorsque vous souhaitez fournir un tri personnalisé ; par exemple, lorsque les valeurs d'une colonne n'ont pas d'ordre de tri naturel ou lorsque l'ordre de tri naturel est inapproprié.  Dans ce cas, vous ne pouvez pas utiliser le tri automatique, mais vous pouvez souhaiter encore que vos utilisateurs puissent trier en cliquant sur les en\-têtes de colonne.  Vous pouvez appeler cette surcharge dans un gestionnaire d'événement <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> si vous n'utilisez pas les en\-têtes de colonne pour la sélection.  
  
> [!NOTE]
>  La surcharge de méthode `Sort(IComparer)` fonctionne uniquement lorsque le contrôle <xref:System.Windows.Forms.DataGridView> n'est pas lié à une source de données externe et que la valeur de propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> est `false`.  Pour personnaliser le tri pour les colonnes liées à une source de données externe, vous devez utiliser les opérations de tri fournies par la source de données.  En mode virtuel, vous devez fournir vos propres opérations de tri pour les colonnes indépendantes.  
  
 Pour utiliser la surcharge de méthode `Sort(IComparer)`, vous devez créer votre propre classe qui implémente l'interface <xref:System.Collections.IComparer>.  Cette interface nécessite que votre classe implémente la méthode <xref:System.Collections.IComparer.Compare%2A?displayProperty=fullName> à laquelle le <xref:System.Windows.Forms.DataGridView> passe des objets <xref:System.Windows.Forms.DataGridViewRow> comme entrée lorsque la surcharge de méthode `Sort(IComparer)` est appelée.  Avec ceci, vous pouvez calculer l'ordre correct des lignes selon les valeurs de n'importe quelle colonne.  
  
 La surcharge de méthode `Sort(IComparer)` ne définit pas les propriétés <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> et <xref:System.Windows.Forms.DataGridView.SortOrder%2A> ; vous devez donc toujours définir la propriété <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName> de façon à afficher le glyphe de tri.  
  
 Comme une alternative à la surcharge de méthode `Sort(IComparer)`, vous pouvez fournir le tri personnalisé en implémentant un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.SortCompare>.  Cet événement se produit lorsque les utilisateurs cliquent sur les en\-têtes de colonnes configurés pour le tri automatique ou lorsque vous appelez la surcharge `Sort(DataGridViewColumn,ListSortDirection)` de la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>.  L'événement se produit pour chaque paire de lignes dans le contrôle, ce qui vous permet de calculer leur ordre correct.  
  
> [!NOTE]
>  L'événement <xref:System.Windows.Forms.DataGridView.SortCompare> ne se produit pas lorsque la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> est définie ou lorsque la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> a la valeur `true`.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=fullName>   
 [Tri des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)   
 [Comment : personnaliser le tri dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)