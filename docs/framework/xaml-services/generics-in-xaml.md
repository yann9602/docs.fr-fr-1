---
title: "Génériques en XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0e5bfb4f327028f09e8c898cf07e5fec9a5f789
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generics-in-xaml"></a>Génériques en XAML
Les Services XAML .NET Framework tel qu’implémenté dans System.Xaml prend en charge l’utilisation des types CLR génériques. Cette prise en charge inclut la spécification de contraintes de génériques comme argument de type et l’application de la contrainte en appelant approprié `Add` méthode pour les cas de collections génériques. Cette rubrique décrit les aspects de l’utilisation et de référencer des types génériques en XAML.  
  
## <a name="xtypearguments"></a>x : TypeArguments  
 `x:TypeArguments`est une directive définie par le langage XAML. Lorsqu’il est utilisé en tant que membre d’un type XAML qui est sauvegardé par un type générique, `x:TypeArguments` passe en limitant les arguments du générique au constructeur de stockage de type. Pour la syntaxe de référence relative aux Services XAML .NET Framework utilisent `x:TypeArguments`, qui inclut des exemples de syntaxe, consultez [Directive x : TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
 Étant donné que `x:TypeArguments` prend une chaîne et a le stockage de convertisseur de type, il est généralement déclaré dans l’utilisation XAML en tant qu’attribut.  
  
 Dans le flux de nœud XAML, les informations déclarées par `x:TypeArguments` peut être obtenu à partir de <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> à un `StartObject` position dans le flux de nœud. La valeur de retour de <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> est une liste de <xref:System.Xaml.XamlType> valeurs. Déterminer si un type XAML représente un type générique peut être effectuée en appelant <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Règles et Conventions de syntaxe pour les génériques en XAML  
 En XAML, un type générique doit toujours être représenté comme un générique contraint ; un générique sans contrainte n’est jamais présent dans le système de type XAML ou un flux de nœud XAML et ne peut pas être représenté dans le balisage XAML. Un générique peut être référencé dans la syntaxe d’attribut XAML, pour les cas où il est une contrainte de type imbriqué d’un générique référencé par `x:TypeArguments`, ou pour les cas où `x:Type` fournit une référence de type CLR pour un type générique. Cela est pris en charge par le biais du <xref:System.Xaml.Schema.XamlTypeTypeConverter> classe définie par les Services XAML .NET Framework.  
  
 Le code XAML activé en forme de la syntaxe d’attribut <xref:System.Xaml.Schema.XamlTypeTypeConverter> modifie le MSIL classique / convention syntaxe CLR qui utilise des crochets pour les types et les contraintes de génériques et substitue à la place des parenthèses pour le conteneur de contrainte. Pour obtenir un exemple, consultez [Directive x : TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Génériques et fonctionnalités XAML 2009  
 Si vous utilisez XAML 2009 au lieu de mapper le CLR des types pour obtenir des types XAML pour les primitives de langage commun de base, vous pouvez utiliser [types intégrés XAML 2009](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) en tant qu’éléments d’informations dans `x:TypeArguments`. Par exemple, vous pouvez déclarer les éléments suivants (non présentés, des mappages de préfixes mais `x` est l’espace de noms XAML du langage XAML 2009) :  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Prise en charge des génériques dans WPF et d’autres infrastructures v3.5  
 Pour l’utilisation de XAML 2006 en ciblant spécifiquement WPF, [x : Class](../../../docs/framework/xaml-services/x-class-directive.md) doit également être fourni dans le même élément que `x:TypeArguments`, et cet élément doit être l’élément racine d’un document XAML. L’élément racine doit mapper à un type générique avec au moins un argument de type. Par exemple <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Les solutions possibles pour prendre en charge des utilisations génériques incluent la définition d’une extension de balisage personnalisée qui peut retourner des types génériques, ou en fournissant un habillage définition qui dérive d’un type générique, mais aplanit la contrainte générique dans sa propre définition de classe de la classe.  
  
 Dans WPF et le ciblage [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], vous pouvez utiliser les fonctionnalités XAML 2009 avec `x:TypeArguments`, mais uniquement pour XAML libre (XAML pas compilé par balisage). Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 Flux de travail personnalisés dans [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] pour [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] ne prennent pas en charge l’utilisation XAML générique.  
  
## <a name="see-also"></a>Voir aussi  
 [x:TypeArguments, directive](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [x:Class, directive](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Types intégrés pour les primitives associées au langage XAML courant](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
