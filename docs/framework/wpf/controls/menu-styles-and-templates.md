---
title: "Styles et mod&#232;les Menu | Microsoft Docs"
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
  - "ControlTemplate (WPF), Menu"
  - "Menu (WPF), styles et modèles"
  - "éléments (WPF), Menu"
  - "états (WPF), Menu"
  - "styles (WPF), Menu"
  - "modèles (WPF), Menu"
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Styles et mod&#232;les Menu
Cette rubrique décrit les styles et les modèles du contrôle <xref:System.Windows.Controls.Menu>.  Vous pouvez modifier le <xref:System.Windows.Controls.ControlTemplate> par défaut pour donner une apparence unique au contrôle.  Pour plus d'informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Composants de Menu  
 Le contrôle <xref:System.Windows.Controls.Menu> ne comporte pas de composants nommés.  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour <xref:System.Windows.Controls.Menu>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.  \(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément de <xref:System.Windows.Controls.Menu> ; <xref:System.Windows.Controls.ScrollViewer> active le défilement dans le contrôle.\)  Si <xref:System.Windows.Controls.ItemsPresenter> n'est pas l'enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer à <xref:System.Windows.Controls.ItemsPresenter> le nom `ItemsPresenter`.  
  
## États de Menu  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.Menu>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## Composants de MenuItem  
 Le tableau ci\-dessous répertorie les composants nommés du contrôle <xref:System.Windows.Controls.Menu>.  
  
||||  
|-|-|-|  
|Élément|Type|Description|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|Zone pour le sous\-menu.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour <xref:System.Windows.Controls.MenuItem>, votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer>.  \(Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément de <xref:System.Windows.Controls.MenuItem> ; <xref:System.Windows.Controls.ScrollViewer> active le défilement dans le contrôle.\)  Si <xref:System.Windows.Controls.ItemsPresenter> n'est pas l'enfant direct du <xref:System.Windows.Controls.ScrollViewer>, vous devez attribuer à <xref:System.Windows.Controls.ItemsPresenter> le nom `ItemsPresenter`.  
  
## États de MenuItem  
 Le tableau suivant répertorie les états visuels du contrôle <xref:System.Windows.Controls.MenuItem>.  
  
||||  
|-|-|-|  
|Nom VisualState|Nom VisualStateGroup|Description|  
|Valid|ValidationStates|Le contrôle utilise la classe <xref:System.Windows.Controls.Validation> et la propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `false`.|  
|InvalidFocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle et a le focus.|  
|InvalidUnfocused|ValidationStates|La propriété jointe de <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> est `true`, a le contrôle, mais n'a pas le focus.|  
  
## ControlTemplate de Menu et MenuItem, exemple  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.Menu>.  
  
 [!code-xml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 L'exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle <xref:System.Windows.Controls.MenuItem>.  
  
 [!code-xml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 L'exemple suivant définit `MenuScrollViewer`, utilisé dans l'exemple précédent.  
  
 [!code-xml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 L'exemple <xref:System.Windows.Controls.ControlTemplate> utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour l'exemple complet, consultez [Style avec ControlTemplates, exemple](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [Personnalisation des contrôles](../../../../docs/framework/wpf/controls/control-customization.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)