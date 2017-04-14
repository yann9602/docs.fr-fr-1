---
title: "x:Key Directive | Microsoft Docs"
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
  - "xKey"
  - "Key"
  - "x:Key"
helpviewer_keywords: 
  - "x:Key attribute [XAML Services]"
  - "Key attribute in XAML [XAML Services]"
  - "XAML [XAML Services], x:Key attribute"
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
caps.latest.revision: 25
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 25
---
# x:Key Directive
Identifie uniquement les éléments qui sont créés et référencés dans un dictionnaire défini en XAML.  L'ajout d'une valeur `x:Key` à un élément d'objet XAML est la méthode la plus courante pour identifier une ressource dans un dictionnaire de ressources, par exemple dans un WPF <xref:System.Windows.ResourceDictionary>.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## Utilisation des attributs XAML \(spécifique à WPF\)  
  
```  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`stringKeyValue`|Chaîne de texte à utiliser comme une clé.  La chaîne de texte doit se conformer à la [XamlName, grammaire](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
|`markupExtensionUsage`|Entre délimiteurs d'extension de balisage {}, utilisation d'extension de balisage qui fournit un objet à utiliser comme clé.  Consultez la section Notes.|  
  
## Notes  
 `x:Key` prend en charge le concept de dictionnaire de ressources XAML.  XAML en tant que langage ne définit pas une implémentation du dictionnaire des ressources, qui est laissée aux infrastructures d'interface utilisateur spécifiques.  Pour en savoir plus sur la façon dont les dictionnaires de ressources XAML sont implémentés dans WPF, consultez [Ressources XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Dans XAML 2006 et WPF, `x:Key` doit être fourni comme un attribut.  Vous pouvez toujours utiliser des clés autres que des chaînes, mais cela requiert qu'une utilisation d'extension de balisage fournisse la valeur autre qu'une chaîne sous la forme d'un attribut.  Lorsque vous utiliserez XAML 2009, `x:Key` peut être spécifié comme un élément, pour prendre en charge explicitement des dictionnaires indexés par les types d'objet autres que des chaînes sans exiger une extension de balisage intermédiaire.  Consultez la section "XAML 2009" dans cette rubrique.  Le reste de la section Notes s'applique spécifiquement à l'implémentation XAML 2006.  
  
 La valeur d'attribut de `x:Key` peut correspondre à n'importe quelle chaîne définie dans la grammaire XamlName \(voir [XamlName, grammaire](../../../docs/framework/xaml-services/xamlname-grammar.md)\) ou à un objet évalué à l'aide d'une extension de balisage.  Consultez les « Remarques sur l'utilisation de WPF » pour obtenir un exemple de WPF.  
  
 Les éléments enfants d'un élément parent correspondant à une implémentation <xref:System.Collections.IDictionary> doivent généralement inclure un attribut `x:Key` qui spécifie une valeur de clé unique dans ce dictionnaire.  Les Frameworks peuvent implémenter des propriétés de clé ajoutées en alias pour remplacer `x:Key` sur les types particuliers ; les types qui définissent de telles propriétés doivent être attribués avec <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Le code équivalent à la spécification de `x:Key` est la clé utilisée pour le <xref:System.Collections.IDictionary> sous\-jacent.  Par exemple, un `x:Key` appliqué au balisage pour une ressource dans  WPF équivaut à la valeur du paramètre `key` de  <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName> lorsque vous ajoutez la ressource à un  <xref:System.Windows.ResourceDictionary> WPF dans le code.  
  
## Remarques sur l'utilisation de WPF  
 Les objets enfants d'un objet parent qui est une implémentation <xref:System.Collections.IDictionary> telle que le <xref:System.Windows.ResourceDictionary> WPF doivent généralement inclure un attribut `x:Key`, et la valeur de clé doit être unique dans ce dictionnaire.  Il existe deux exceptions notables :  
  
-   Certains types WPF déclarent une clé implicite pour l'utilisation de dictionnaire.  Par exemple, un <xref:System.Windows.Style> avec un <xref:System.Windows.Style.TargetType%2A>, ou un <xref:System.Windows.DataTemplate> avec un <xref:System.Windows.DataTemplate.DataType%2A>, peut être placé dans un <xref:System.Windows.ResourceDictionary> et être utilisé la clé implicite.  
  
-   WPF prend en charge un concept de dictionnaire de ressources fusionnées.  Les clés peuvent être partagées entre les dictionnaires fusionnés, et le comportement de clé partagée peut être accédé à l'aide de <xref:System.Windows.FrameworkContentElement.FindResource%2A>.  Pour plus d'informations, consultez [Dictionnaires de ressources fusionnés](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Dans le modèle d'application et l'implémentation XAML WPF globale, l'unicité de la clé n'est pas vérifiée par le compilateur de balisage XAML.  Au lieu de cela, les valeurs manquantes ou non uniques de `x:Key` provoquent des erreurs de chargement de l'analyseur XAML.  Toutefois, la gestion par [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] des dictionnaires pour WPF peut souvent noter ces erreurs pendant la phase de conception.  
  
 Dans la syntaxe affichée, l'objet <xref:System.Windows.ResourceDictionary> est implicite dans la façon dont le processeur WPF XAML produit une collection pour remplir une collection <xref:System.Windows.FrameworkElement.Resources%2A>.  <xref:System.Windows.ResourceDictionary> n'est généralement pas fourni de manière explicite en tant qu'élément dans le balisage, bien qu'il puisse l'être à des fins de clarté \(il s'agirait alors d'un élément objet de collection entre l'élément de propriété <xref:System.Windows.FrameworkElement.Resources%2A> et les éléments qu'il contient qui remplissent le dictionnaire\).  Pour plus d'informations sur la raison pour laquelle un objet de collection est presque toujours un élément implicite dans le balisage, consultez [Syntaxe XAML en détail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Dans l'implémentation XAML WPF, la gestion pour les clés de dictionnaire de ressources est définie par la classe abstraite <xref:System.Windows.ResourceKey>.  Toutefois, le processeur WPF XAML produit différents types d'extension sous\-jacents pour les clés en fonction de leur utilisation.  Par exemple, la clé d'un <xref:System.Windows.DataTemplate> ou de classes dérivées est gérée séparément et produit un objet <xref:System.Windows.DataTemplateKey> distinct.  
  
 Les clés et les noms utilisent des directives et des éléments de langage différents \(`x:Key` contre `x:Name`\) dans la définition XAML de base.  Les clés et les noms sont également utilisés dans des situations différentes par la définition WPF et l'application de ces concepts.  Pour plus d'informations, consultez [Portées de nom XAML WPF](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 Comme indiqué précédemment, la valeur d'une clé peut être fournie via une extension de balisage et peut être différente d'une valeur de chaîne.  Un exemple de scénario WPF est que la valeur de `x:Key` peut être un [ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).  Certains contrôles exposent une clé de style de ce type pour une ressource de style personnalisée qui influence une partie de l'apparence et du comportement de ce contrôle sans remplacer le style totalement.  <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> constitue un exemple d'une clé de ce type.  
  
 La fonctionnalité de dictionnaire fusionné WPF ajoute des considérations supplémentaires concernant l'unicité clé et le comportement de recherche clé.  Pour plus d'informations, consultez [Dictionnaires de ressources fusionnés](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
## XAML 2009  
 XAML 2009 assouplit la restriction spécifiant que `x:Key` doit toujours être fourni sous forme d'attribut.  
  
 Dans WPF, vous pouvez utiliser des fonctionnalités XAML 2009, mais uniquement pour le XAML non compilé par balisage.  Le XAML compilé par balisage pour WPF et la forme de langage BAML de XAML ne prend actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 En XAML 2009, vous pouvez spécifier des éléments `x:Key` via l'utilisation suivante :  
  
### Utilisation de l'élément XAML \(XAML 2009 uniquement\)  
  
```  
<object>  
  <x:Key>  
     keyObject  
  </x:Key>  
...  
</object>  
```  
  
### Valeurs XAML  
  
|||  
|-|-|  
|`keyObject`|Élément objet de l'objet utilisé comme clé pour un `object` donné dans un dictionnaire spécialisé.|  
  
-   Le conteneur\/parent de ce type d'utilisation n'est pas affiché ici.  `object` est censé être un enfant d'un type d'élément objet qui représente une implémentation de dictionnaire spécialisé.  `keyObject` est supposé être une instance de l'objet \(ou une valeur d'un type valeur\) qui est appropriée comme clé pour cette implémentation de dictionnaire spécialisée particulière.  
  
-   WPF n'implémente pas les dictionnaires qui requièrent cette utilisation.  Les clés d'objet correspondent davantage à une fonctionnalité générale du langage XAML, qui peut s'avérer utile pour certains scénarios de dictionnaire personnalisé où la création du dictionnaire en langage XAML est souhaitable.  Pour les fonctionnalités WPF telles que les styles implicites qui utilisent des clés de non\-chaîne pour les ressources, d'autres techniques pour l'établissement ou la spécification des clés existent, l'utilisation d'une clé d'objet ainsi n'est pas nécessaire.  
  
-   *keyObject* pourrait être également une utilisation d'une extension de balisage dans le formulaire d'élément objet, plutôt qu'une instance de l'objet directe.  
  
## Notes d'utilisation de Silverlight  
 `x:Key` pour Silverlight est documenté séparément.  Pour plus d'informations, consultez [Fonctionnalités de langage d'espace de noms XAML \(x :\) \(Silverlight\) \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## Voir aussi  
 [Ressources XAML](../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Ressources et code](../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [StaticResource, extension de balisage](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)