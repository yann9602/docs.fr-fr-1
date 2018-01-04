---
title: "Styles et modèles DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5fd9b374f9e2c367daa9869862ab717828049887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid-styles-and-templates"></a>Styles et modèles DataGrid
Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.DataGrid> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datagrid-parts"></a>Composants de DataGrid  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.DataGrid> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|La ligne qui contient les en-têtes de colonne.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.DataGrid>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> au sein d’un <xref:System.Windows.Controls.ScrollViewer>. (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans le <xref:System.Windows.Controls.DataGrid>; le <xref:System.Windows.Controls.ScrollViewer> permet le défilement dans le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de la <xref:System.Windows.Controls.ScrollViewer>, vous devez donner le <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.  
  
 Le modèle par défaut pour le <xref:System.Windows.Controls.DataGrid> contient un <xref:System.Windows.Controls.ScrollViewer> contrôle. Pour plus d’informations sur les composants définis par le <xref:System.Windows.Controls.ScrollViewer>, consultez [ScrollViewer Styles et modèles](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>États de DataGrid  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.DataGrid> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagridcell-parts"></a>Composants de DataGridCell  
 Le <xref:System.Windows.Controls.DataGridCell> élément n’a pas de composants nommés.  
  
## <a name="datagridcell-states"></a>États de DataGridCell  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.DataGridCell> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur la cellule.|  
|Avec focus|FocusStates|La cellule a le focus.|  
|Sans focus|FocusStates|La cellule n’a pas le focus|  
|Actuel|CurrentStates|La cellule est la cellule active.|  
|Normale|CurrentStates|La cellule n’est pas la cellule active.|  
|Afficher|InteractionStates|La cellule est en mode d’affichage.|  
|Modification|InteractionStates|La cellule est en mode édition.|  
|Selected|SelectionStates|La cellule est sélectionnée.|  
|Non sélectionné|SelectionStates|La cellule n’est pas sélectionnée.|  
|InvalidFocused|ValidationStates|La cellule n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|La cellule n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|La cellule est valide.|  
  
## <a name="datagridrow-parts"></a>Composants de DataGridRow  
 Le <xref:System.Windows.Controls.DataGridRow> élément n’a pas de composants nommés.  
  
## <a name="datagridrow-states"></a>États de DataGridRow  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.DataGridRow> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur la ligne.|  
|MouseOver_Editing|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est en mode édition.|  
|MouseOver_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est sélectionnée.|  
|MouseOver_Unfocused_Editing|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est en mode édition et n’a pas le focus.|  
|MouseOver_Unfocused_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est sélectionnée et n’a pas le focus.|  
|Normal_AlternatingRow|CommonStates|La ligne est une ligne en alternance.|  
|Normal_Editing|CommonStates|La ligne est en mode édition.|  
|Normal_Selected|CommonStates|La ligne est sélectionnée.|  
|Unfocused_Editing|CommonStates|La ligne est en mode édition et n’a pas le focus.|  
|Unfocused_Selected|CommonStates|La ligne est sélectionnée et n’a pas le focus.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagridrowheader-parts"></a>Composants de DataGridRowHeader  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Primitives.DataGridRowHeader> élément.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|L’élément qui est utilisé pour redimensionner l’en-tête de ligne à partir du haut.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|L’élément qui est utilisé pour redimensionner l’en-tête de ligne à partir du bas.|  
  
## <a name="datagridrowheader-states"></a>États de DataGridRowHeader  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.DataGridRowHeader> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur la ligne.|  
|MouseOver_CurrentRow|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est la ligne actuelle.|  
|MouseOver_CurrentRow_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est en cours et sélectionné.|  
|MouseOver_EditingRow|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est en mode édition.|  
|MouseOver_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est sélectionnée.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est en cours et sélectionné et n’a pas le focus.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est en mode édition et n’a pas le focus.|  
|MouseOver_Unfocused_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est sélectionnée et n’a pas le focus.|  
|Normal_CurrentRow|CommonStates|La ligne est la ligne actuelle.|  
|Normal_CurrentRow_Selected|CommonStates|La ligne est la ligne active et est sélectionnée.|  
|Normal_EditingRow|CommonStates|La ligne est en mode édition.|  
|Normal_Selected|CommonStates|La ligne est sélectionnée.|  
|Unfocused_CurrentRow_Selected|CommonStates|La ligne est la ligne active est sélectionnée et n’a pas le focus.|  
|Unfocused_EditingRow|CommonStates|La ligne est en mode édition et n’a pas le focus.|  
|Unfocused_Selected|CommonStates|La ligne est sélectionnée et n’a pas le focus.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>Composants de DataGridColumnHeadersPresenter  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> élément.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|L’espace réservé pour les en-têtes de colonne.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>États de DataGridColumnHeadersPresenter  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|InvalidFocused|ValidationStates|La cellule n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|La cellule n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|La cellule est valide.|  
  
## <a name="datagridcolumnheader-parts"></a>Parties DataGridColumnHeader  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> élément.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|L’élément qui est utilisé pour redimensionner l’en-tête de colonne à partir de la gauche.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|L’élément qui est utilisé pour redimensionner l’en-tête de colonne à droite.|  
  
## <a name="datagridcolumnheader-states"></a>États de DataGridColumnHeader  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le contrôle.|  
|Appuyé|CommonStates|Le contrôle est enfoncé.|  
|SortAscending|SortStates|La colonne est triée par ordre croissant.|  
|SortDescending|SortStates|La colonne est triée par ordre décroissant.|  
|Non triées|SortStates|La colonne n’est pas triée.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagrid-controltemplate-example"></a>Exemple de ControlTemplate de DataGrid  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.DataGrid> contrôle et ses types associés.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
