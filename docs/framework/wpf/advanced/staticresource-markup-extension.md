---
title: "StaticResource, extension de balisage | Microsoft Docs"
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
  - "StaticResource"
  - "StaticResourceExtension"
helpviewer_keywords: 
  - "StaticResource (extensions de balisage)"
  - "XAML, StaticResource (extension de balisage)"
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# StaticResource, extension de balisage
Fournit une valeur pour tout attribut de propriété [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en recherchant une référence à une ressource déjà définie.  Le comportement de recherche de cette ressource est analogue à la recherche au moment du chargement, qui recherche des ressources chargées auparavant à partir de la balise de la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] actuelle, ainsi que d'autres sources d'application, et génère cette valeur de ressource comme valeur de propriété dans les objets au moment de l'exécution.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{StaticResource key}" .../>  
```  
  
## Utilisation d'éléments objet XAML  
  
```  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`key`|Clé de la ressource demandée.  Cette clé est assignée initialement par le [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md) si une ressource est créée dans la balise ou est fournie comme paramètre `key` lors de l'appel de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> si la ressource est créée dans le code.|  
  
## Notes  
  
> [!IMPORTANT]
>  Une `StaticResource` ne doit pas tenter de faire une référence vers l'avant à une ressource définie d'un point de vue lexical dans le fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Ce type de tentative n'est pas pris en charge, et même si une telle référence n'échoue pas, la tentative de référence vers l'avant entraînera une altération des performances au moment du chargement lors de la recherche des tables de hachage internes représentant un <xref:System.Windows.ResourceDictionary>.  Pour optimiser les résultats, ajustez la composition de vos dictionnaires de ressources de manière à éviter les références vers l'avant.  Si vous ne pouvez pas éviter une référence vers l'avant, utilisez [DynamicResource, extension de balisage](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) à la place.  
  
 La <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> spécifiée doit correspondre à une ressource existante, identifiée par un [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md) à un endroit quelconque dans votre page, l'application, les thèmes de contrôle et ressources externes disponibles ou les ressources système.  La recherche de ressources s'effectue dans cet ordre.  Pour plus d'informations sur le comportement de la recherche de ressources statiques et dynamiques, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Une clé de ressource peut être une chaîne quelconque définie dans la [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md).  Elle peut également être un autre type d'objet, tel qu'un <xref:System.Type>.  Une clé <xref:System.Type> joue un rôle déterminant dans la manière dont les contrôles peuvent prendre la forme de thèmes, par le biais d'une clé de style implicite.  Pour plus d'informations, consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Une ressource peut également être référencée de manière déclarative par le biais de [DynamicResource, extension de balisage](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.  Le jeton de chaîne fourni après la chaîne d'identificateur `StaticResource` est assigné en tant que valeur <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> de la classe d'extension <xref:System.Windows.StaticResourceExtension> sous\-jacente.  
  
 `StaticResource` peut être utilisé dans la syntaxe d'élément objet.  Dans ce cas, la valeur de la propriété <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> doit être spécifiée.  
  
 `StaticResource` peut également être employé dans une utilisation d'attribut en clair qui spécifie la propriété <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> en tant que paire propriété\=valeur :  
  
```  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.  `StaticResource` ne comportant qu'une seule propriété définissable \(obligatoire\), cette utilisation en clair n'est pas classique.  
  
 Dans l'implémentation de processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.StaticResourceExtension>.  
  
 `StaticResource` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  Toutes les extensions de balisage en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d'attributs. Cette convention indique au convertisseur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que l'extension de balisage doit traiter l'attribut.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## Voir aussi  
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Ressources et code](../../../../docs/framework/wpf/advanced/resources-and-code.md)