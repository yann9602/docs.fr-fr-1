---
title: "ComponentResourceKey, extension de balisage | Microsoft Docs"
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
  - "ComponentResourceKey"
  - "ComponentResourceKeyExtension"
helpviewer_keywords: 
  - "ComponentResourceKey (extension de balisage)"
  - "XAML, ComponentResourceKey (extension de balisage)"
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# ComponentResourceKey, extension de balisage
Définit et référence des clés pour des ressources chargées à partir d'assemblys externes.  Cela permet à une recherche de ressources de spécifier un type cible dans un assembly, plutôt qu'un dictionnaire de ressources explicite dans un assembly ou une classe.  
  
## Utilisation des attributs XAML \(définition de clé, compact\)  
  
```  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## Utilisation d'attributs XAML \(définition de clé, détaillé\)  
  
```  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## Utilisation d'attributs XAML \(demande de ressource, compact\)  
  
```  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## Utilisation d'attributs XAML \(demande de ressource, détaillé\)  
  
```  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`targetTypeName`|Nom du type [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] public défini dans l'assembly de ressource.|  
|`targetID`|Clé pour la ressource.  Lors de la recherche de ressources, `targetID` équivaut au [x:Key, directive](../../../../docs/framework/xaml-services/x-key-directive.md) de la ressource.|  
  
## Notes  
 Comme indiqué dans les utilisations ci\-dessus, une utilisation d'une extension de balisage {`ComponentResourceKey` } se trouve à deux endroits :  
  
-   Définition d'une clé dans un dictionnaire de ressources du thème, tel que fourni par un auteur de contrôle.  
  
-   Accès à une ressource du thème à partir de l'assembly, lorsque vous redéfinissez le modèle du contrôle mais souhaitez utiliser les valeurs de propriété qui viennent de ressources fournies par les thèmes du contrôle.  
  
 Pour le référencement des ressources de composant qui proviennent de thèmes, il est recommandé en général que vous utilisiez `{DynamicResource}` plutôt que `{StaticResource}`.  Cela s'affiche dans les utilisations.  `{DynamicResource}` est recommandé parce que le thème lui\-même peut être modifié par l'utilisateur.  Si vous voulez la ressource de composant qui correspond le plus à l'intention de contrôle de l'auteur pour la prise en charge d'un thème, vous devez permettre à votre référence de ressource de composant d'être également dynamique.  
  
 Le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifie un type qui existe dans l'assembly cible où la ressource est réellement définie.  Vous pouvez définir et utiliser une `ComponentResourceKey` que vous sachiez ou non exactement où le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> est défini. Elle doit toutefois finalement résoudre le type via les assemblys référencés.  
  
 La <xref:System.Windows.ComponentResourceKey> est souvent utilisée pour définir des clés qui sont ensuite exposées comme membres d'une classe.  Pour cela, utilisez le constructeur de classe <xref:System.Windows.ComponentResourceKey>, et non l'extension de balisage.  Pour plus d'informations, consultez <xref:System.Windows.ComponentResourceKey>, ou la section « Définition et référencement de clés pour les ressources de thème » de la rubrique [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Pour établir des clés et référencer des ressources de clé, la syntaxe d'attributs est utilisée communément pour l'extension de balisage `ComponentResourceKey`.  
  
 La syntaxe compacte indiquée s'appuie sur la signature de constructeur <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=fullName> et l'utilisation du paramètre positionnel d'une extension de balisage.  L'ordre dans lequel le `targetTypeName` et le `targetID` sont donnés est important.  La syntaxe détaille repose sur le constructeur <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=fullName> par défaut, puis définit <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> et <xref:System.Windows.ComponentResourceKey.ResourceId%2A> à la manière d'une syntaxe d'attribut réelle sur un élément objet.  Dans la syntaxe détaillée, l'ordre dans lequel les propriétés sont définies n'est pas important.  La relation et les mécanismes de cette alternative \(compacte et détaillée\) sont décrits plus en détails dans la rubrique [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Techniquement, la valeur de `targetID` peut être n'importe quel objet ; elle ne doit pas nécessairement être une chaîne.  Toutefois, l'utilisation la plus courante de WPF est d'aligner la valeur `targetID` avec les formulaires qui sont des chaînes, où ces chaînes sont valides dans le [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey` peut être utilisé dans la syntaxe d'élément objet.  Dans ce cas, il convient de spécifier la valeur des propriétés <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> et <xref:System.Windows.ComponentResourceKey.ResourceId%2A> pour initialiser correctement l'extension.  
  
 Dans l'implémentation du lecteur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la gestion de cette extension de balisage est définie par la classe <xref:System.Windows.ComponentResourceKey>.  
  
 `ComponentResourceKey` est une extension de balisage.  Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d'attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l'exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés.  Toutes les extensions de balisage en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d'attributs. Cette convention indique au convertisseur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que l'extension de balisage doit traiter l'attribut.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## Voir aussi  
 <xref:System.Windows.ComponentResourceKey>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)