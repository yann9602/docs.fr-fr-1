---
title: x:Static, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d006c8d0937a454dcbe092dcc3e35c4644088e59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xstatic-markup-extension"></a>x:Static, extension de balisage
Fait référence à une entité de code en valeur statique qui est définie dans un [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]– moyen conforme. La propriété statique qui est référencée peut être utilisée pour fournir la valeur d’une propriété en XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`prefix`|Facultatif. Un préfixe qui fait référence à un espace de noms XAML mappé, non définis par défaut. `prefix`est affiché explicitement dans l’utilisation parce que vous référencez rarement des propriétés statiques qui proviennent d’un espace de noms XAML par défaut. Consultez la section Notes.|  
|`typeName`|Obligatoire. Le nom du type qui définit le membre statique souhaité.|  
|`staticMemberName`|Obligatoire. Le nom du membre de valeur statique souhaitée (une constante, une propriété statique, un champ ou une valeur d’énumération).|  
  
## <a name="remarks"></a>Remarques  
 L’entité de code référencée doit être une des opérations suivantes :  
  
-   Une constante  
  
-   Une propriété statique  
  
-   Un champ  
  
-   Une valeur d’énumération  
  
 Spécifiant toute autre entité de code, comme une propriété non statique, de provoque une erreur de compilation si le code XAML est compilé par balisage, ou une exception de l’analyse au moment du chargement XAML.  
  
 Vous pouvez apporter `x:Static` des références à des champs statiques ou des propriétés qui ne sont pas dans l’espace de noms XAML par défaut pour le document XAML en cours ; Toutefois, cela nécessite un mappage de préfixe. Espaces de noms XAML sont presque toujours définies sur l’élément racine du document XAML.  
  
 Les opérations de recherche pour les propriétés statiques peuvent être effectuées par les Services XAML .NET Framework et ses lecteurs XAML et les writers XAML, quand elles sont exécutées avec le contexte de schéma XAML par défaut. Ce contexte de schéma XAML peut utiliser la réflexion CLR pour fournir les valeurs statiques nécessaires pour la construction de graphique d’objet. Le `typeName` vous spécifiez est en fait un nom de type XAML, pas un nom de type CLR, bien qu’il s’agit essentiellement le même nom lorsque vous utilisez le contexte de schéma XAML par défaut ou lors de l’utilisation de toutes les infrastructures d’implémentation XAML basé sur CLR existants.  
  
 Soyez prudent lorsque vous apportez `x:Static` références qui ne sont pas directement le type de valeur d’une propriété. Dans le code XAML du traitement de séquence, les valeurs fournie d’une extension de balisage n’appellent pas une conversion de valeur supplémentaires. Cela est vrai même si votre `x:Static` référence crée une chaîne de texte et une conversion de valeur pour les valeurs d’attribut basé sur la chaîne de texte, généralement se produit pour ce membre spécifique ou pour des valeurs de membre de type de retour.  
  
 La syntaxe d'attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d'identificateur `x:Static` est assigné en tant que valeur <xref:System.Windows.Markup.StaticExtension.Member%2A> de la classe d'extension <xref:System.Windows.Markup.StaticExtension> sous-jacente.  
  
 Il existe deux autres utilisations de code XAML qui sont techniquement possibles. Toutefois, ces utilisations sont moins courantes, car elles sont inutilement détaillés :  
  
 **Syntaxe d’élément de l’objet :** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName``" .../>`  
  
 **Syntaxe d’attribut avec la propriété de membre explicite pour la chaîne d’initialisation :** `<` `object`  ``  `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName``}" .../>`  
  
 Dans l’implémentation de Services XAML .NET Framework, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Markup.StaticExtension> classe.  
  
 `x:Static` est une extension de balisage. Toutes les extensions de balisage en cours d’utilisation XAML le `{` et `}` caractères dans leur syntaxe d’attribut, qui est la convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit fournir une valeur. Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Notes d’utilisation WPF  
 L’espace de noms XAML par défaut vous utilisez pour la programmation WPF ne contient pas de nombreuses propriétés statiques utiles, et la plupart des propriétés statiques utiles prennent en charge tels que les convertisseurs de type qui facilitent l’utilisation sans nécessiter de `{x:Static}` . Pour les propriétés statiques, vous devez mapper un préfixe pour un espace de noms XAML si une des conditions suivantes est remplie :  
  
-   Vous référencez un type qui existe dans WPF, mais ne fait pas partie de l’espace de noms XAML par défaut pour WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Il s’agit d’un scénario assez courant d’utilisation `x:Static`. Par exemple, vous pouvez utiliser un `x:Static` référence avec un mappage d’espace de noms XAML à le <xref:System> assembly CLR d’espace de noms et mscorlib pour référencer les propriétés statiques de la <xref:System.Environment> classe.  
  
-   Vous référencez un type d’un assembly personnalisé.  
  
-   Vous référencez un type qui existe dans un assembly WPF, mais ce type est dans un espace de noms CLR qui n’a pas été mappé comme faisant partie de l’espace de noms WPF par défaut. Le mappage des espaces de noms CLR dans l’espace de noms XAML par défaut pour WPF est exécuté par les définitions dans les différents assemblys WPF (pour plus d’informations sur ce concept, consultez [espaces de noms XAML et mappage Namespace pour XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Espaces de noms CLR non mappés peuvent exister si cet espace de noms CLR est composé principalement de définitions de classe qui sont généralement pas prévues pour XAML, tels que <xref:System.Windows.Threading>.  
  
 Pour plus d’informations sur l’utilisation des préfixes et espaces de noms XAML pour WPF, consultez [espaces de noms XAML et Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [x:Type, extension de balisage](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Types migrés de WPF vers System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
