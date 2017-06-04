---
title: "Styles et mod&#232;les DataGrid | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ControlTemplate (WPF), DataGrid"
  - "DataGrid (WPF), styles et modèles"
  - "éléments (WPF), DataGrid"
  - "états (WPF), DataGrid"
  - "styles (WPF), DataGrid"
  - "modèles (WPF), DataGrid"
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Styles et mod&#232;les DataGrid
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.DataGrid>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de DataGrid  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.DataGrid>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Ligne qui contient les en\-têtes de colonnes.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour <xref:System.Windows.Controls.DataGrid>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.  \(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément de <xref:System.Windows.Controls.DataGrid> ; <xref:System.Windows.Controls.ScrollViewer> active le défilement dans le contrôle.\)  Si <xref:System.Windows.Controls.ItemsPresenter> n'est pas l'enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer à <xref:System.Windows.Controls.ItemsPresenter> le nom `ItemsPresenter`.  
  
 Le modèle par défaut pour le <xref:System.Windows.Controls.DataGrid> contient un contrôle <xref:System.Windows.Controls.ScrollViewer>.  Pour plus d'informations sur les composants définis dans <xref:System.Windows.Controls.ScrollViewer>, consultez [Styles et modèles ScrollViewer](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md).  
  
## États de DataGrid  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.DataGrid>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|Le contrôle est désactivé.|  
|InvalidFocused|ValidationStates|Le contrôle n'est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n'est pas valide et n'a pas le focus.|  
|Valid|ValidationStates|Le contrôle est valide.|  
  
## Composants de DataGridCell  
 L'élément <xref:System.Windows.Controls.DataGridCell> ne comporte pas de composants nommés.  
  
## États de DataGridCell  
 Le tableau suivant répertorie les états visuels de l'élément <xref:System.Windows.Controls.DataGridCell>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur la cellule.|  
|Focused|FocusStates|La cellule a le focus.|  
|Unfocused|FocusStates|La cellule n'a pas le focus.|  
|Actuelle|CurrentStates|La cellule est la cellule active.|  
|Normale|CurrentStates|La cellule n'est pas la cellule active.|  
|Affichage|InteractionStates|La cellule est en mode d'affichage.|  
|Modification|InteractionStates|La cellule est en mode d'édition.|  
|Sélectionné|SelectionStates|La cellule est sélectionnée.|  
|Non sélectionné|SelectionStates|La cellule n'est pas sélectionnée.|  
|InvalidFocused|ValidationStates|La cellule n'est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|La cellule n'est pas valide et n'a pas le focus.|  
|Valid|ValidationStates|La cellule est valide.|  
  
## Composants de DataGridRow  
 L'élément <xref:System.Windows.Controls.DataGridRow> ne comporte pas de composants nommés.  
  
## États de DataGridRow  
 Le tableau suivant répertorie les états visuels de l'élément <xref:System.Windows.Controls.DataGridRow>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur la ligne.|  
|MouseOver\_Editing|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est en mode d'édition.|  
|MouseOver\_Selected|CommonStates|Le pointeur de souris est positionné sur la ligne et la ligne est sélectionnée.|  
|MouseOver\_Unfocused\_Editing|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est en mode d'édition et n'a pas le focus.|  
|MouseOver\_Unfocused\_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est sélectionnée et n'a pas le focus.|  
|Normal\_AlternatingRow|CommonStates|La ligne est une ligne alternée.|  
|Normal\_Editing|CommonStates|La ligne est en mode d'édition.|  
|Normal\_Selected|CommonStates|La ligne est sélectionnée.|  
|Unfocused\_Editing|CommonStates|La ligne est en mode d'édition et n'a pas le focus.|  
|Unfocused\_Selected|CommonStates|La ligne est sélectionnée et n'a pas le focus.|  
|InvalidFocused|ValidationStates|Le contrôle n'est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n'est pas valide et n'a pas le focus.|  
|Valid|ValidationStates|Le contrôle est valide.|  
  
## Composants de DataGridRowHeader  
 Le tableau ci\-dessous répertorie les composants nommés de l'élément <xref:System.Windows.Controls.Primitives.DataGridRowHeader>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l'en\-tête de ligne à partir du début.|  
|PART\_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l'en\-tête de ligne à partir de la fin.|  
  
## États de DataGridRowHeader  
 Le tableau suivant répertorie les états visuels de l'élément <xref:System.Windows.Controls.Primitives.DataGridRowHeader>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur la ligne.|  
|MouseOver\_CurrentRow|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est la ligne active.|  
|MouseOver\_CurrentRow\_Selected|CommonStates|Le pointeur de souris est positionné sur la ligne, et la ligne est active et sélectionnée.|  
|MouseOver\_EditingRow|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est en mode d'édition.|  
|MouseOver\_Selected|CommonStates|Le pointeur de souris est positionné sur la ligne et la ligne est sélectionnée.|  
|MouseOver\_Unfocused\_CurrentRow\_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est active, sélectionnée et n'a pas le focus.|  
|MouseOver\_Unfocused\_EditingRow|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est en mode d'édition et n'a pas le focus.|  
|MouseOver\_Unfocused\_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est sélectionnée et n'a pas le focus.|  
|Normal\_CurrentRow|CommonStates|La ligne est la ligne active.|  
|Normal\_CurrentRow\_Selected|CommonStates|La ligne est la ligne active et est sélectionnée.|  
|Normal\_EditingRow|CommonStates|La ligne est en mode d'édition.|  
|Normal\_Selected|CommonStates|La ligne est sélectionnée.|  
|Unfocused\_CurrentRow\_Selected|CommonStates|La ligne est la ligne active, est sélectionnée et n'a pas le focus.|  
|Unfocused\_EditingRow|CommonStates|La ligne est en mode d'édition et n'a pas le focus.|  
|Unfocused\_Selected|CommonStates|La ligne est sélectionnée et n'a pas le focus.|  
|InvalidFocused|ValidationStates|Le contrôle n'est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n'est pas valide et n'a pas le focus.|  
|Valid|ValidationStates|Le contrôle est valide.|  
  
## Composants de DataGridColumnHeadersPresenter  
 Le tableau ci\-dessous répertorie les composants nommés de l'élément <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Espace réservé pour les en\-têtes de colonnes.|  
  
## États de DataGridColumnHeadersPresenter  
 Le tableau suivant répertorie les états visuels de l'élément <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|InvalidFocused|ValidationStates|La cellule n'est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|La cellule n'est pas valide et n'a pas le focus.|  
|Valid|ValidationStates|La cellule est valide.|  
  
## Composants de DataGridColumnHeader  
 Le tableau ci\-dessous répertorie les composants nommés de l'élément <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l'en\-tête de colonne à partir de la gauche.|  
|PART\_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l'en\-tête de colonne à partir de la droite.|  
  
## États de DataGridColumnHeader  
 Le tableau suivant répertorie les états visuels de l'élément <xref:System.Windows.Controls.Primitives.DataGridColumnHeader>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Pressed|CommonStates|Le contrôle est enfoncé.|  
|SortAscending|SortStates|La colonne est triée dans l'ordre croissant.|  
|SortDescending|SortStates|La colonne est triée dans l'ordre décroissant.|  
|Unsorted|SortStates|La colonne n'est pas triée.|  
|InvalidFocused|ValidationStates|Le contrôle n'est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n'est pas valide et n'a pas le focus.|  
|Valid|ValidationStates|Le contrôle est valide.|  
  
## DataGrid ControlTemplate, exemple  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.DataGrid> et ses types associés.  
  
 [!code-xml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 L'exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour l'exemple complet, consultez          [Style avec ControlTemplates, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160041) .  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)