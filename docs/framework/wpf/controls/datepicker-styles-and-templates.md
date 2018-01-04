---
title: "Styles et modèles DatePicker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4683ebd66afb2d4ac5bfa615336787c4006b4335
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datepicker-styles-and-templates"></a>Styles et modèles DatePicker
Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.DatePicker> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="datepicker-parts"></a>Composants de DatePicker  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.DatePicker> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|La racine du contrôle.|  
|PART_Button|<xref:System.Windows.Controls.Button>|Le bouton qui ouvre et ferme le <xref:System.Windows.Controls.Calendar>.|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|La zone de texte qui vous permet d’entrer une date.|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|La fenêtre contextuelle pour le <xref:System.Windows.Controls.DatePicker> contrôle.|  
  
## <a name="datepicker-states"></a>États de DatePicker  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.DatePicker> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.DatePicker> est désactivé.|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="datepickertextbox-parts"></a>Parties DatePickerTextBox  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Primitives.DatePickerTextBox> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|L’élément qui contient le texte initial dans le <xref:System.Windows.Controls.DatePicker>.|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|Un élément visuel qui peut contenir un <xref:System.Windows.FrameworkElement>. Le texte de la <xref:System.Windows.Controls.TextBox> s’affiche dans cet élément.|  
  
## <a name="datepickertextbox-states"></a>États de DatePickerTextBox  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.DatePickerTextBox> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.Primitives.DatePickerTextBox> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|ReadOnly|CommonStates|L’utilisateur ne peut pas modifier le texte dans le <xref:System.Windows.Controls.Primitives.DatePickerTextBox>.|  
|Avec focus|FocusStates|Le contrôle a le focus.|  
|Sans focus|FocusStates|Le contrôle n’a pas le focus.|  
|Limite supérieure|WatermarkStates|Le contrôle affiche son texte d’origine.  Le <xref:System.Windows.Controls.Primitives.DatePickerTextBox> est dans l’état lorsque l’utilisateur n’a pas entré du texte ou de la date sélectionnée.|  
|Unwatermarked|WatermarkStates|L’utilisateur a entré du texte dans le <xref:System.Windows.Controls.Primitives.DatePickerTextBox> ou sélectionné une date dans le <xref:System.Windows.Controls.DatePicker>.|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate, exemple  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.DatePicker> contrôle.  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
