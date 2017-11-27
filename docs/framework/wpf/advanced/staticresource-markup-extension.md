---
title: StaticResource, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 821cd152ccb7a02dda5338d6a3ec44d6625c0097
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="staticresource-markup-extension"></a>StaticResource, extension de balisage
Fournit une valeur pour tout [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribut de propriété en recherchant une référence à une ressource déjà définie. Comportement de recherche de cette ressource est analogue à la recherche au moment du chargement, qui recherche des ressources qui ont été précédemment chargées à partir du balisage d’actuel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page ainsi que d’autres sources d’application et génère cette valeur de ressource en tant que le valeur de propriété dans les objets d’exécution.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`key`|La clé pour la ressource demandée. Cette clé a été initialement affectée par le [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) si une ressource a été créée dans la balise ou est fournie comme le `key` paramètre lors de l’appel <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> si la ressource a été créée dans le code.|  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]
>  A `StaticResource` ne devez pas tenter de faire une référence vers l’avant à une ressource qui est définie lexical dans le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier. Tente de faire n’est pas pris en charge, et même si une telle référence n’échoue pas, la tentative de référence vers l’avant entraînera une baisse des performances temps charge lorsque les tables de hachage interne représentant un <xref:System.Windows.ResourceDictionary> sont recherchés. Pour de meilleurs résultats, ajustez la composition de vos dictionnaires de ressources de manière à éviter les références vers l’avant. Si vous ne pouvez pas éviter une référence vers l’avant, utilisez [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) à la place.  
  
 Spécifié <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> doit correspondre à une ressource existante, identifiée par un [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) à un niveau dans votre page, application, thèmes de contrôle disponibles et ressources externes ou ressources système. La recherche de ressource se produit dans cet ordre. Pour plus d’informations sur le comportement de recherche de ressources statiques et dynamiques, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Une clé de ressource peut être n’importe quelle chaîne définie dans le [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md). Une clé de ressource peut être également les autres types d’objet, comme un <xref:System.Type>. A <xref:System.Type> clé est essentielle à Comment contrôles peuvent être un style thèmes, via une clé de style implicite. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 L’autre moyen déclaratif de référencement d’une ressource est un [DynamicResource Markup Extension](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d'identificateur `StaticResource` est assigné en tant que valeur <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> de la classe d'extension <xref:System.Windows.StaticResourceExtension> sous-jacente.  
  
 `StaticResource`peut être utilisé dans la syntaxe d’élément objet. Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> propriété est requise.  
  
 `StaticResource` peut également être utilisé dans une utilisation d'attributs en clair qui spécifie la propriété <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> en tant que paire propriété=valeur :  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 L'utilisation en clair est souvent utile pour les extensions qui comportent plusieurs propriétés définissables ou si certaines propriétés sont facultatives. 
          `StaticResource` ne comportant qu'une seule propriété définissable (obligatoire), cette utilisation en clair n'est pas classique.  
  
 Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation du processeur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.StaticResourceExtension> classe.  
  
 `StaticResource` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Ressources et code](../../../../docs/framework/wpf/advanced/resources-and-code.md)
