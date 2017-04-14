---
title: "TemplateBinding, extension de balisage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TemplateBinding"
  - "TemplateBindingExtension"
helpviewer_keywords: 
  - "TemplateBinding (extensions de balisage)"
  - "XAML, TemplateBinding (extension de balisage)"
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# TemplateBinding, extension de balisage
Cette extension lie la valeur d'une propriété dans un modèle de contrôle afin de la définir comme valeur d'une autre propriété exposée dans le contrôle basé sur un modèle.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## Utilisation d'attributs XAML \(pour la propriété de méthode setter dans le modèle ou le style\)  
  
```  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`propertyName`|<xref:System.Windows.DependencyProperty.Name%2A?displayProperty=fullName> de la propriété définie dans la syntaxe de méthode setter.|  
|`sourceProperty`|Autre propriété de dépendance qui existe sur le type basé sur un modèle, spécifiée par <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=fullName>.<br /><br /> \- ou \-<br /><br /> Nom de propriété « dotted\-down » défini par un autre type que le type de cible basé sur un modèle.  Il s'agit en réalité d'un <xref:System.Windows.PropertyPath>.  Consultez [PropertyPath, syntaxe XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## Notes  
 Un `TemplateBinding` est une version optimisée d'une [Liaison](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) pour les scénarios de modèle, similaire à un `Binding` construit avec `{Binding RelativeSource={RelativeSource TemplatedParent}}`.  `TemplateBinding` est toujours une liaison unidirectionnelle, même si les propriétés ont comme valeur par défaut des liaisons bidirectionnelles.  Les deux propriétés doivent toutes être des propriétés de dépendance.  
  
 [RelativeSource](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) est une autre extension de balisage parfois utilisée avec ou au lieu de `TemplateBinding` afin d'effectuer une liaison de propriété relative dans un modèle.  
  
 Cette rubrique ne décrit pas le concept des modèles de contrôle. Pour plus d'informations, consultez [Styles et modèles Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md).  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.  Le jeton de chaîne fourni après la chaîne d'identificateur `TemplateBinding` est assigné en tant que valeur <xref:System.Windows.TemplateBindingExtension.Property%2A> de la classe d'extension <xref:System.Windows.TemplateBindingExtension> sous\-jacente.  
  
 La syntaxe d'élément objet est possible, mais elle n'est pas indiquée car elle ne possède aucune application réaliste.  `TemplateBinding` est utilisé pour remplir des valeurs dans des méthodes setter, à l'aide d'expressions évaluées. En outre, l'utilisation de la syntaxe d'élément objet de `TemplateBinding` pour remplir la syntaxe des éléments de propriété `<Setter.Property>` est inutilement détaillée.  
  
 `TemplateBinding` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.TemplateBindingExtension.Property%2A> en tant que paire propriété\=valeur :  
  
```  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.  `TemplateBinding` ne comportant qu'une seule propriété définissable \(obligatoire\), cette utilisation en clair n'est pas classique.  
  
 Dans l'implémentation de processeur XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.TemplateBindingExtension>.  
  
 `TemplateBinding` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  En XAML, toutes les extensions de balisage utilisent les caractères `{` et `}` dans leur syntaxe d'attributs, convention selon laquelle un processeur XAML reconnaît qu'une extension de balisage doit traiter l'attribut.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## Voir aussi  
 <xref:System.Windows.Style>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [RelativeSource, extension de balisage](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md)   
 [Binding, extension de balisage](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)