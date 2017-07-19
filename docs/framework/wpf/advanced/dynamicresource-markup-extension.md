---
title: "DynamicResource, extension de balisage | Microsoft Docs"
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
  - "DynamicResource"
  - "DynamicResourceExtension"
helpviewer_keywords: 
  - "DynamicResource (extensions de balisage)"
  - "XAML, DynamicResource (extension de balisage)"
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# DynamicResource, extension de balisage
Fournit la valeur de tout attribut de propriété [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en différant la recherche d'une valeur comme référence à une ressource définie.  Le comportement de recherche de cette ressource est analogue à la recherche au moment de l'exécution.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{DynamicResource key}" .../>  
```  
  
## Utilisation des éléments de propriété XAML  
  
```  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`key`|Clé de la ressource demandée.  Cette clé est assignée initialement par le [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md) si une ressource est créée dans la balise ou est fournie comme paramètre `key` lors de l'appel de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> si la ressource est créée dans le code.|  
  
## Notes  
 Un `DynamicResource` créera une expression temporaire pendant la compilation initiale et donc diffèrera la recherche des ressources jusqu'à ce que la valeur de ressource demandée soit effectivement requise pour construire un objet.  Cela peut se faire potentiellement après que la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a été chargée.  La valeur de ressource sera recherchée selon une recherche clé dans tous les dictionnaires de ressources actifs, à partir de la portée de page actuelle, et est remplacée par l'expression d'espace réservé dans la compilation.  
  
> [!IMPORTANT]
>  En termes de priorité des propriétés de dépendance, une expression `DynamicResource` est équivalente à la position à laquelle est appliquée la référence à une ressource dynamique.  Si vous définissez une valeur locale pour une propriété qui avait précédemment une expression `DynamicResource` comme valeur locale, `DynamicResource` est complètement supprimé.  Pour plus d'informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Certains scénarios d'accès aux ressources sont particulièrement appropriés pour `DynamicResource`, par opposition à [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  Consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) pour la description des mérites relatifs et implications de performance de `DynamicResource` et `StaticResource`.  
  
 Le <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> spécifié doit correspondre à une ressource existante déterminée par [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md) à quelque niveau que ce soit dans votre page, application, thèmes de contrôle disponibles et ressources externes ou ressources système ; les ressources seront recherchées dans cet ordre.  Pour plus d'informations sur la recherche de ressources statiques et dynamiques, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Une clé de ressource peut être une chaîne quelconque définie dans [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md).  Elle peut également être tout autre type d'objet, tel qu'un <xref:System.Type>.  Une clé <xref:System.Type> est un facteur fondamental déterminant la manière dont les contrôles peuvent être appelés par des thèmes.  Pour plus d'informations, consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] pour la recherche de valeurs de ressource, telles que <xref:System.Windows.FrameworkElement.FindResource%2A>, suit la même logique de recherche de ressource que celle utilisée par `DynamicResource`.  
  
 Une ressource peut également être référencée de manière déclarative par le biais de [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage.  Le jeton de chaîne fourni après la chaîne d'identificateur `DynamicResource` est assigné en tant que valeur <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> de la classe d'extension <xref:System.Windows.DynamicResourceExtension> sous\-jacente.  
  
 `DynamicResource` peut être utilisé dans la syntaxe d'élément objet.  Dans ce cas, la valeur de la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> doit être spécifiée.  
  
 `DynamicResource` peut également être employé dans une utilisation d'attribut en clair qui spécifie la propriété <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> en tant que paire propriété\=valeur :  
  
```  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives.  `DynamicResource` ne comportant qu'une seule propriété définissable \(obligatoire\), cette utilisation en clair n'est pas classique.  
  
 Dans l'implémentation de processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.DynamicResourceExtension>.  
  
 `DynamicResource` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  Toutes les extensions de balisage en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d'attributs. Cette convention indique au convertisseur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que l'extension de balisage doit traiter l'attribut.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## Voir aussi  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Ressources et code](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)