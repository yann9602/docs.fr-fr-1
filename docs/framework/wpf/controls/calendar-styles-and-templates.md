---
title: "Styles et modèles Calendar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b27049c63faa9bf84dc5febd210a29a530f175a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="calendar-styles-and-templates"></a>Styles et modèles Calendar
Cette rubrique décrit les styles et modèles pour la <xref:System.Windows.Controls.Calendar> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour donner une apparence unique au contrôle. Pour plus d’informations, consultez [Personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## <a name="calendar-parts"></a>Éléments de calendrier  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Calendar> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Le mois actuellement affiché ou une année sur le <xref:System.Windows.Controls.Calendar>.|  
|PART_Root|<xref:System.Windows.Controls.Panel>|Le panneau de configuration qui contient la <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## <a name="calendar-states"></a>États de calendrier  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Calendar> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|----------------------|---------------------------|-----------------|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendaritem-parts"></a>Composants de CalendarItem  
 Le tableau suivant répertorie les composants nommés pour le <xref:System.Windows.Controls.Primitives.CalendarItem> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|La racine du contrôle.|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|Le bouton qui affiche la page précédente du calendrier lorsque vous cliquez dessus.|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|Le bouton qui affiche la page suivante du calendrier lorsque vous cliquez dessus.|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|Le bouton qui permet de basculer entre le mode mois, année et décennie.|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|Héberge le contenu en mode mois.|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|Héberge le contenu en mode année ou décennie.|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|Le segment de recouvrement de l’état désactivé.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|Le <xref:System.Windows.DataTemplate> qui décrit la structure visuelle.|  
  
## <a name="calendaritem-states"></a>États de CalendarItem  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.CalendarItem> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|État normal|CommonStates|État par défaut.|  
|État désactivé|CommonStates|L’état du calendrier lors de la <xref:System.Windows.UIElement.IsEnabled%2A> propriété est `false`.|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendardaybutton-parts"></a>Composant de CalendarDayButton  
 Le <xref:System.Windows.Controls.Primitives.CalendarDayButton> contrôle n’a pas de composants nommés.  
  
## <a name="calendardaybutton-states"></a>États de CalendarDayButton  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.CalendarDayButton> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarDayButton> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Appuyé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarDayButton> est enfoncé.|  
|Selected|SelectionStates|Le bouton est sélectionné.|  
|Non sélectionné|SelectionStates|Le bouton n’est pas sélectionné.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Le bouton a le focus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Le bouton n’a pas le focus.|  
|Avec focus|FocusStates|Le bouton a le focus.|  
|Sans focus|FocusStates|Le bouton n’a pas le focus.|  
|Actif|ActiveStates|Le bouton est actif.|  
|Inactif|ActiveStates|Le bouton est inactif.|  
|RegularDay|DayStates|Le bouton ne représente pas <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|Aujourd'hui|DayStates|Le bouton représente <xref:System.DateTime.Today%2A?displayProperty=nameWithType>.|  
|NormalDay|BlackoutDayStates|Le bouton représente un jour qui peut être sélectionné.|  
|BlackoutDay|BlackoutDayStates|Le bouton représente un jour qui ne peuvent pas être sélectionné.|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendarbutton-parts"></a>Composants de CalendarButton  
 Le <xref:System.Windows.Controls.Primitives.CalendarButton> contrôle n’a pas de composants nommés.  
  
## <a name="calendarbutton-states"></a>Les États CalendarButton  
 Le tableau suivant répertorie les états visuels pour le <xref:System.Windows.Controls.Primitives.CalendarButton> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normale|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarButton> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur le <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Appuyé|CommonStates|Le <xref:System.Windows.Controls.Primitives.CalendarButton> est enfoncé.|  
|Selected|SelectionStates|Le bouton est sélectionné.|  
|Non sélectionné|SelectionStates|Le bouton n’est pas sélectionné.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Le bouton a le focus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Le bouton n’a pas le focus.|  
|Avec focus|FocusStates|Le bouton a le focus.|  
|Sans focus|FocusStates|Le bouton n’a pas le focus.|  
|Actif|ActiveStates|Le bouton est actif.|  
|Inactif|ActiveStates|Le bouton est inactif.|  
|Valide|ValidationStates|Le contrôle utilise le <xref:System.Windows.Controls.Validation> classe et le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `false`.|  
|InvalidFocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle a le focus.|  
|InvalidUnfocused|ValidationStates|Le <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriété jointe est `true` a le contrôle n’a pas le focus.|  
  
## <a name="calendar-controltemplate-example"></a>Exemple de ControlTemplate de calendrier  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour la <xref:System.Windows.Controls.Calendar> contrôle et les types associés.  
  
 [!code-xaml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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
