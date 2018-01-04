---
title: "Styles et modèles TreeView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea6e7d26ad70eef3aae4678b922ef01bccc9450b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="treeview-styles-and-templates"></a>Styles et modèles TreeView
Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.TreeView> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="treeview-parts"></a>Composants de TreeView  
 Le <xref:System.Windows.Controls.TreeView> contrôle n’a pas de composants nommés.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.TreeView>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> au sein d’un <xref:System.Windows.Controls.ScrollViewer>. (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans le <xref:System.Windows.Controls.TreeView>; le <xref:System.Windows.Controls.ScrollViewer> permet le défilement dans le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de la <xref:System.Windows.Controls.ScrollViewer>, vous devez donner le <xref:System.Windows.Controls.ItemsPresenter> le nom, `ItemsPresenter`.  
  
## <a name="treeview-states"></a>États de TreeView  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.TreeView> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="treeviewitem-parts"></a>Composants de TreeViewItem  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.TreeViewItem> contrôle.  
  
|Élément|Type|Description|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|Un élément visuel qui contient cet en-tête de contenu de la <xref:System.Windows.Controls.TreeView> contrôle.|  
  
## <a name="treeviewitem-states"></a>États de TreeViewItem  
 Le tableau suivant répertorie les états visuels <xref:System.Windows.Controls.TreeViewItem> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Normale|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.TreeViewItem>.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.TreeViewItem> est désactivé.|  
|Avec focus|FocusStates|Le <xref:System.Windows.Controls.TreeViewItem> a le focus.|  
|Sans focus|FocusStates|Le <xref:System.Windows.Controls.TreeViewItem> n’a pas le focus.|  
|Développé|ExpansionStates|Le <xref:System.Windows.Controls.TreeViewItem> contrôle est développé.|  
|Réduit|ExpansionStates|Le <xref:System.Windows.Controls.TreeViewItem> contrôle est réduit.|  
|HasItems|HasItemsStates|Le <xref:System.Windows.Controls.TreeViewItem> a des éléments.|  
|NoItems|HasItemsStates|Le <xref:System.Windows.Controls.TreeViewItem> n’a pas d’éléments.|  
|Selected|SelectionStates|Le <xref:System.Windows.Controls.TreeViewItem> est sélectionnée.|  
|SelectedInactive|SelectionStates|Le <xref:System.Windows.Controls.TreeViewItem> est sélectionné mais pas actif.|  
|Non sélectionné|SelectionStates|Le <xref:System.Windows.Controls.TreeViewItem> n’est pas sélectionnée.|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate, exemple  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.TreeView> contrôle et ses types associés.  
  
 [!code-xaml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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
