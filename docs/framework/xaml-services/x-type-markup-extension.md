---
title: x:Type, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4d645d5c953c0ff33435a5648024ace099455e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xtype-markup-extension"></a>x:Type, extension de balisage
Fournit le CLR <xref:System.Type> objet qui est le type sous-jacent pour un type XAML spécifié.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`prefix`|Facultatif. Un préfixe qui mappe un espace de noms XAML par défaut. Définition d’un préfixe n’est généralement pas nécessaire. Consultez la section Notes.|  
|`typeNameValue`|Obligatoire. Un nom de type peut être résolu à l’espace de noms XAML par défaut en cours ; ou spécifié préfixe mappé si `prefix` est fourni.|  
  
## <a name="remarks"></a>Notes  
 Le `x:Type` extension de balisage a une fonction semblable à la `typeof()` opérateur dans [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] ou `GetType` opérateur dans [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].  
  
 Le `x:Type` extension de balisage fournit un comportement de conversion de chaînes pour les propriétés qui prennent le type <xref:System.Type>. L’entrée est un type XAML. La relation entre le type XAML d’entrée et la sortie CLR <xref:System.Type> est que la sortie <xref:System.Type> est la <xref:System.Xaml.XamlType.UnderlyingType%2A> de l’entrée <xref:System.Xaml.XamlType>, après avoir recherché le nécessaire <xref:System.Xaml.XamlType> selon le contexte de schéma XAML et le <xref:System.Windows.Markup.IXamlTypeResolver>le contexte de service.  
  
 Dans les Services XAML .NET Framework, la gestion de cette extension de balisage est définie par le <xref:System.Windows.Markup.TypeExtension> classe.  
  
 Dans les implémentations d’infrastructure spécifiques, certaines propriétés qui acceptent <xref:System.Type> comme une valeur accepte directement le nom du type (la valeur de chaîne du type `Name`). Toutefois, l’implémentation de ce comportement est un scénario complexe. Pour obtenir des exemples, consultez la section « Remarques sur l’utilisation WPF » qui suit.  
  
 La syntaxe d’attribut est la syntaxe la plus couramment utilisée avec cette extension de balisage. Le jeton de chaîne fourni après la chaîne d'identificateur `x:Type` est assigné en tant que valeur <xref:System.Windows.Markup.TypeExtension.TypeName%2A> de la classe d'extension <xref:System.Windows.Markup.TypeExtension> sous-jacente. Dans le contexte de schéma XAML par défaut pour les Services XAML .NET Framework, qui est basé sur les types CLR, la valeur de cet attribut est le <xref:System.Reflection.MemberInfo.Name%2A> du type souhaité, ou qui contient <xref:System.Reflection.MemberInfo.Name%2A> précédé d’un préfixe pour un espace de noms XAML par défaut mappage.  
  
 Le `x:Type` extension de balisage peut être utilisée dans la syntaxe d’élément objet. Dans ce cas, en spécifiant la valeur de la <xref:System.Windows.Markup.TypeExtension.TypeName%2A> propriété est requise pour initialiser correctement l’extension.  
  
 Le `x:Type` extension de balisage peut également servir comme attribut brut ; toutefois cette utilisation n’est pas classique : `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## <a name="wpf-usage-notes"></a>Notes d’utilisation WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Namespace XAML et le mappage de Type par défaut  
 L’espace de noms XAML par défaut pour la programmation WPF contient la plupart des types XAML, que vous avez besoin pour les scénarios XAML standard. Par conséquent, vous pouvez souvent éviter des préfixes lors du référencement de valeurs de type XAML. Vous devrez peut-être mapper un préfixe si vous référencez un type d’un assembly personnalisé ou pour les types qui existent dans un assembly WPF mais qui sont dans un espace de noms CLR qui n’a pas été mappé à l’espace de noms XAML par défaut. Pour plus d’informations sur les préfixes d’espaces de noms XAML et les espaces de noms CLR mappage, consultez [espaces de noms XAML et mappage Namespace pour XAML WPF](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Cette prise en charge Typename en tant que chaîne de propriétés de type  
 WPF prend en charge des techniques permettant la spécification de la valeur de certaines propriétés de type <xref:System.Type> sans nécessiter une `x:Type` extension de balisage. Au lieu de cela, vous pouvez spécifier la valeur sous forme de chaîne qui désigne le type. Des exemples sont <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> et <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Prise en charge pour ce comportement n’est pas fournie par les convertisseurs de type ou les extensions de balisage. Au lieu de cela, il s’agit d’un comportement de report implémenté par le biais <xref:System.Windows.FrameworkElementFactory>.  
  
 Silverlight prend en charge une convention similaire. En fait, Silverlight ne prend pas en charge `{x:Type}` dans sa prise en charge du langage XAML et n’accepte pas `{x:Type}` utilisations en dehors de quelques cas qui sont destinés à prendre en charge la migration de XAML WPF-Silverlight. Par conséquent, le comportement typename-as-string est intégré à l’évaluation de propriété native de Silverlight tous les où un <xref:System.Type> est la valeur.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 fournit la prise en charge supplémentaire pour les types génériques et modifie le comportement de la fonctionnalité de `x:TypeArguments` et `x:Type` pour fournir cette prise en charge.  
  
-   `x:TypeArguments`et l’élément objet associé pour une instanciation d’objet générique peut être sur des éléments autres que la racine. Pour plus d’informations, consultez la section « XAML 2009 » de [Directive x : TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 prend en charge une syntaxe permettant de spécifier la contrainte d’un type générique dans le balisage. Cela peut être utilisé par `x:TypeArguments`, par `x:Type`, ou par les deux fonctionnalités conjointement.  
  
-   Implémentation XAML WPF lors du traitement de XAML 2009 pour le chargement ajoute également cette fonctionnalité pour le comportement de conversion de type implicite pour certaines propriétés d’infrastructure qui utilisent le type <xref:System.Type>.  
  
 Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour XAML libre (XAML pas compilé par balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Style>  
 [Application d’un style et création de modèles](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensions de balisage et XAML WPF](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
