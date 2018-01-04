---
title: ComponentResourceKey, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4bfaee35ba9f8cf60deb01c52a142433d08021c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey, extension de balisage
Définit et référence des clés pour les ressources qui sont chargés à partir des assemblys externes. Cela permet une recherche de ressource spécifier un type de cible dans un assembly, plutôt qu’un dictionnaire de ressources explicite dans un assembly ou une classe.  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>Utilisation d’attributs XAML (définition de clé, compacte)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>Utilisation d’attributs XAML (définition de clé, détaillé)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>Utilisation d’attributs XAML (demande de ressource, compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>Utilisation d’attributs XAML (demande de ressource, détaillé)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`targetTypeName`|Le nom public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type qui est défini dans l’assembly de ressources.|  
|`targetID`|La clé pour la ressource. Lors de la recherche de ressources, `targetID` sera similaire à la [x : Key, Directive](../../../../docs/framework/xaml-services/x-key-directive.md) de la ressource.|  
  
## <a name="remarks"></a>Notes  
 Comme indiqué dans les utilisations ci-dessus, un {`ComponentResourceKey`} extension de balisage se trouve dans deux emplacements :  
  
-   La définition d’une clé dans un dictionnaire de ressources de thème, tel que fourni par un auteur de contrôle.  
  
-   L’accès à une ressource du thème à partir de l’assembly, lorsque vous apprêter le contrôle mais souhaitez utiliser les valeurs de propriété qui viennent de ressources fournies par les thèmes du contrôle.  
  
 Pour faire référence à des ressources de composant qui proviennent de thèmes, il est généralement recommandé d’utiliser `{DynamicResource}` plutôt que `{StaticResource}`. Cela est illustré dans les utilisations. `{DynamicResource}`est recommandée car le thème lui-même peut être modifié par l’utilisateur. Si vous souhaitez que la ressource de composant qui correspond le mieux à l’intention de l’auteur de contrôle pour un thème de prise en charge, vous devez activer votre référence de ressource de composant d’être également dynamique.  
  
 Le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifie un type qui existe dans l’assembly cible où la ressource est définie. A `ComponentResourceKey` peut être définie et utilisée indépendamment de savoir exactement où le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> est défini, mais par la suite doit résoudre le via les assemblys référencés.  
  
 Une utilisation commune pour <xref:System.Windows.ComponentResourceKey> consiste à définir des clés qui sont ensuite exposées en tant que membres d’une classe. Pour cela, vous utilisez la <xref:System.Windows.ComponentResourceKey> constructeur de classe, pas l’extension de balisage. Pour plus d’informations, consultez <xref:System.Windows.ComponentResourceKey>, ou la section « Définition et référencement de clés pour les ressources de thème » de la rubrique [vue d’ensemble de la création de contrôle](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Pour établir des clés et faisant référence à des ressources de clé, la syntaxe d’attribut est généralement utilisée pour le `ComponentResourceKey` extension de balisage.  
  
 La syntaxe compacte indiquée s’appuie sur la <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> signature de constructeur et l’utilisation des paramètres positionnels d’une extension de balisage. L’ordre dans lequel le `targetTypeName` et `targetID` figurent est important. La syntaxe détaillée s’appuie sur le <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructeur par défaut, puis définit la <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> et <xref:System.Windows.ComponentResourceKey.ResourceId%2A> d’une manière analogue à la syntaxe d’attribut réelle sur un élément objet. Dans la syntaxe détaillée, l’ordre dans lequel les propriétés sont définies n’est pas important. La relation et les mécanismes de cette alternative (compacte et détaillée) est décrite plus en détail dans la rubrique [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Techniquement, la valeur de `targetID` peut être n’importe quel objet, il n’a pas à être une chaîne. Toutefois, l’utilisation la plus courante dans WPF est d’aligner les `targetID` valeur avec les formulaires qui sont des chaînes, et où ces chaînes sont valides dans le [XamlName, grammaire](../../../../docs/framework/xaml-services/xamlname-grammar.md).  
  
 `ComponentResourceKey`peut être utilisé dans la syntaxe d’élément objet. Dans ce cas, en spécifiant la valeur des deux le <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> et <xref:System.Windows.ComponentResourceKey.ResourceId%2A> propriétés est requis pour initialiser correctement l’extension.  
  
 Dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implémentation de lecteur, la gestion de cette extension de balisage est définie par le <xref:System.Windows.ComponentResourceKey> classe.  
  
 `ComponentResourceKey` est une extension de balisage. Les extensions de balisage sont généralement implémentées pour éviter que les valeurs d’attribut ne soient autre chose que des valeurs littérales ou des noms de gestionnaire et lorsque l’exigence dépasse le cadre de la définition de convertisseurs de type sur certains types ou propriétés. Toutes les extensions de balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent les caractères { et } dans leur syntaxe d’attribut, convention selon laquelle un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reconnaît qu’une extension de balisage doit traiter l’attribut. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
