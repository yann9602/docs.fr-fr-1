---
title: "Styles et mod&#232;les Calendar | Microsoft Docs"
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
  - "Calendar (WPF), styles et modèles"
  - "ControlTemplate (WPF), Calendar"
  - "éléments (WPF), Calendar"
  - "états (WPF), Calendar"
  - "styles (WPF), Calendar"
  - "modèles (WPF), Calendar"
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Styles et mod&#232;les Calendar
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Calendar>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de Calendar  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.Calendar>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|Mois ou année actuellement affiché dans <xref:System.Windows.Controls.Calendar>.|  
|PART\_Root|<xref:System.Windows.Controls.Panel>|Panneau qui contient <xref:System.Windows.Controls.Primitives.CalendarItem>.|  
  
## États de Calendar  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.Calendar>.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|---------------------|--------------------------|-----------------|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Composants de CalendarItem  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_Root|<xref:System.Windows.FrameworkElement>|Racine du contrôle.|  
|PART\_PreviousButton|<xref:System.Windows.Controls.Button>|Bouton qui affiche la page précédente du calendrier lorsque l'utilisateur clique dessus.|  
|PART\_NextButton|<xref:System.Windows.Controls.Button>|Bouton qui affiche la page suivante du calendrier lorsque l'utilisateur clique dessus.|  
|PART\_HeaderButton|<xref:System.Windows.Controls.Button>|Bouton qui permet de basculer le mode entre mois, année et décennie.|  
|PART\_MonthView|<xref:System.Windows.Controls.Grid>|Héberge le contenu en mode mois.|  
|PART\_YearView|<xref:System.Windows.Controls.Grid>|Héberge le contenu en mode année ou décennie.|  
|PART\_DisabledVisual|<xref:System.Windows.FrameworkElement>|Superposition de l'état désactivé.|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate> qui décrit la structure visuelle.|  
  
## États de CalendarItem  
 Le tableau ci\-dessous répertorie les états visuels du contrôle <xref:System.Windows.Controls.Primitives.CalendarItem>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|L'état du calendrier lorsque la propriété <xref:System.Windows.UIElement.IsEnabled%2A> a la valeur `false`.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Composant de CalendarDayButton  
 Le contrôle <xref:System.Windows.Controls.Primitives.CalendarDayButton> ne comporte pas de composants nommés.  
  
## États de CalendarDayButton  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.Primitives.CalendarDayButton>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur <xref:System.Windows.Controls.Primitives.CalendarDayButton>.|  
|Pressed|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> est enfoncé.|  
|Sélectionné|SelectionStates|Le bouton est sélectionné.|  
|Non sélectionné|SelectionStates|Le bouton n'est pas sélectionné.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Le bouton a le focus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Le bouton n'a pas le focus.|  
|Focused|FocusStates|Le bouton a le focus.|  
|Unfocused|FocusStates|Le bouton n'a pas le focus.|  
|Active|ActiveStates|Le bouton est actif.|  
|Inactif|ActiveStates|Le bouton est inactif.|  
|RegularDay|DayStates|Le bouton ne représente pas <xref:System.DateTime.Today%2A?displayProperty=fullName>.|  
|Today|DayStates|Le bouton représente <xref:System.DateTime.Today%2A?displayProperty=fullName>.|  
|NormalDay|BlackoutDayStates|Le bouton représente un jour qui peut être sélectionné.|  
|BlackoutDay|BlackoutDayStates|Le bouton représente un jour qui ne peut pas être sélectionné.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Composants de CalendarButton  
 Le contrôle <xref:System.Windows.Controls.Primitives.CalendarButton> ne comporte pas de composants nommés.  
  
## États de CalendarButton  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.Primitives.CalendarButton>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Normal|CommonStates|État par défaut.|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> est désactivé.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur <xref:System.Windows.Controls.Primitives.CalendarButton>.|  
|Pressed|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> est enfoncé.|  
|Sélectionné|SelectionStates|Le bouton est sélectionné.|  
|Non sélectionné|SelectionStates|Le bouton n'est pas sélectionné.|  
|CalendarButtonFocused|CalendarButtonFocusStates|Le bouton a le focus.|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|Le bouton n'a pas le focus.|  
|Focused|FocusStates|Le bouton a le focus.|  
|Unfocused|FocusStates|Le bouton n'a pas le focus.|  
|Active|ActiveStates|Le bouton est actif.|  
|Inactif|ActiveStates|Le bouton est inactif.|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Calendar ControlTemplate, exemple  
 L'exemple suivant indique comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Calendar> et ses types associés.  
  
 [!code-xml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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