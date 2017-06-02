---
title: "Diff&#233;rences entre les contr&#244;les DataGridView et DataGrid Windows Forms | Microsoft Docs"
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
  - "grilles de données"
  - "DataGrid (contrôle Windows Forms), comparaison avec le contrôle DataGridView"
  - "DataGridView (contrôle Windows Forms), comparaison avec le contrôle DataGrid"
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Diff&#233;rences entre les contr&#244;les DataGridView et DataGrid Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> est un nouveau contrôle qui remplace le contrôle <xref:System.Windows.Forms.DataGrid>.  Le contrôle <xref:System.Windows.Forms.DataGridView> fournit de nombreux éléments de base et des fonctionnalités avancées qui manquent dans le contrôle <xref:System.Windows.Forms.DataGrid>.  En outre, l'architecture du contrôle <xref:System.Windows.Forms.DataGridView> fait qu'il est beaucoup plus facile à étendre et à personnaliser que le contrôle <xref:System.Windows.Forms.DataGrid>.  
  
 Le tableau suivant décrit quelques\-unes des fonctionnalités principales disponibles dans le contrôle <xref:System.Windows.Forms.DataGridView>, et qui font défaut dans le contrôle <xref:System.Windows.Forms.DataGrid>.  
  
|Fonctionnalités du contrôle DataGridView|Description|  
|----------------------------------------------|-----------------|  
|Plusieurs types de colonne|Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plus de types de colonne intégré que le contrôle <xref:System.Windows.Forms.DataGrid>.  Ces types de colonne répondent aux besoins de la plupart des scénarios courants, mais sont également plus faciles à étendre ou à remplacer que les types de colonne du contrôle <xref:System.Windows.Forms.DataGrid>.  Pour plus d'informations, consultez [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs façons d'afficher des données|Le contrôle <xref:System.Windows.Forms.DataGrid> est limité au niveau de l'affichage de données d'une source de données externe.  Toutefois, le contrôle <xref:System.Windows.Forms.DataGridView> peut afficher des données indépendantes stockées dans le contrôle, des données provenant d'une source de données liée, ou à la fois des données dépendantes et indépendantes.  Vous pouvez également implémenter le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView> pour fournir une gestion de données personnalisée.  Pour plus d'informations, consultez [Modes d'affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs façons de personnaliser l'affichage des données|Le contrôle <xref:System.Windows.Forms.DataGridView> fournit beaucoup de propriétés et d'événements qui vous permettent de spécifier la façon dont les données sont mises en forme et affichées.  Par exemple, vous pouvez modifier l'apparence des cellules, des lignes et des colonnes selon les données qu'elles contiennent, ou vous pouvez remplacer des données d'un certain type de données par des données équivalentes d'un autre type.  Pour plus d'informations, consultez [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs options pour modifier l'apparence et le comportement des cellules, des lignes, des colonnes et des en\-têtes|Le contrôle <xref:System.Windows.Forms.DataGridView> vous permet de travailler avec les composants de grille individuels de plusieurs façons différentes.  Par exemple, vous pouvez figer des lignes et des colonnes pour les empêcher de défiler ; masquer des lignes, des colonnes et des en\-têtes ; modifier la manière dont les lignes, les colonnes et les tailles sont ajustées ; modifier la façon dont les utilisateurs effectuent des sélections ; et fournir des info\-bulles et des menus contextuels pour les différentes cellules, lignes et colonnes.|  
  
 Le contrôle <xref:System.Windows.Forms.DataGrid> est conservé à des fins de compatibilité descendante et pour des besoins particuliers.  Vous devez presque toujours utiliser le contrôle <xref:System.Windows.Forms.DataGridView>.  La seule fonctionnalité qui est disponible dans le <xref:System.Windows.Forms.DataGrid> contrôle et non disponible dans le contrôle <xref:System.Windows.Forms.DataGridView> est l'affichage hiérarchique d'informations de deux tables connexes dans un seul contrôle.  Vous devez utiliser deux contrôles <xref:System.Windows.Forms.DataGridView> pour afficher des informations de deux tables qui sont dans une relation maître\/détail.  
  
## Mise à niveau au contrôle DataGridView  
 Si vous possédez des applications existantes qui utilisent le contrôle <xref:System.Windows.Forms.DataGrid> dans un scénario simple lié aux données sans personnalisations, vous pouvez remplacer simplement l'ancien contrôle par le nouveau contrôle.  Dns la mesure où les deux contrôles utilisent l'architecture standard de liaison de données Windows Forms, le contrôle <xref:System.Windows.Forms.DataGridView> affiche vos données dépendantes sans nécessiter une configuration supplémentaire.  Vous pouvez, toutefois, souhaiter tirer parti des améliorations de la liaison de données en liant vos données à un composant <xref:System.Windows.Forms.BindingSource>, que vous pouvez lier ensuite au contrôle <xref:System.Windows.Forms.DataGridView>.  Pour plus d'informations, consultez [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).  
  
 Puisque le contrôle <xref:System.Windows.Forms.DataGridView> a une architecture entièrement nouvelle, il n'existe aucun chemin d'accès de conversion simple vous permettant d'utiliser des personnalisations <xref:System.Windows.Forms.DataGrid> avec le contrôle <xref:System.Windows.Forms.DataGridView>.  Beaucoup de personnalisations <xref:System.Windows.Forms.DataGrid> sont, cependant, inutiles avec le contrôle <xref:System.Windows.Forms.DataGridView> en raison des fonctionnalités intégrées disponibles dans le nouveau contrôle.  Si vous avez créé pour le contrôle <xref:System.Windows.Forms.DataGrid> des types de colonne personnalisés que vous souhaitez utiliser avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous devez les implémenter de nouveau à l'aide de la nouvelle architecture.  Pour plus d'informations, consultez [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGrid>   
 <xref:System.Windows.Forms.BindingSource>   
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Modes d'affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)   
 [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)   
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)   
 [Modes de tri des colonnes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [Modes de sélection dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)   
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)