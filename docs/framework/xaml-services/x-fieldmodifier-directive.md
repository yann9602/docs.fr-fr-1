---
title: x:FieldModifier, directive
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ed50dd2aff1702543789f06939f7c2bc4b3dd83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier, directive
Modifie le comportement de compilation XAML afin que les champs pour les références d’objet nommé sont définis avec <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> accéder à la place de la <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> comportement par défaut.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|*Public*|La chaîne exacte que vous passez pour spécifier <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varie selon le langage de programmation de code-behind qui est utilisé. Consultez la section Notes.|  
  
## <a name="dependencies"></a>Dépendances  
 Si une production XAML utilise `x:FieldModifier` n’importe où, l’élément racine de cette production XAML doit déclarer un [x : Class Directive](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Notes  
 `x:FieldModifier`n’est pas pertinent pour déclarer le niveau d’accès général d’une classe ou de ses membres. Il ne s’applique uniquement pour le comportement de traitement XAML lorsqu’un objet XAML particulier qui fait partie d’une production XAML est traité et devienne un objet qui est potentiellement accessible dans le graphique d’objets d’une application. Par défaut, la référence de champ pour un tel objet reste privée, ce qui empêche les consommateurs du contrôle de modifier le graphique d’objets directement. Au lieu de cela, les consommateurs de contrôle sont attendus pour modifier le graphique d’objets à l’aide de modèles standard qui sont activées par les modèles de programmation, comme en obtenant des collections d’éléments, les propriétés publiques dédiées, la racine de disposition, l’enfant et ainsi de suite.  
  
 La valeur de la `x:FieldModifier` attribut varie selon le langage de programmation et son objectif peut varier dans les infrastructures spécifiques. La chaîne à utiliser dépend de la façon dont chaque langage implémente ses <xref:System.CodeDom.Compiler.CodeDomProvider> et les convertisseurs de type qu’il retourne pour définir les significations de <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> et <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, et si cette langue est respecte la casse.  
  
-   Pour [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est `public`.  
  
-   Pour [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], la chaîne à passer pour désigner <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> est `Public`.  
  
-   Pour [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], n’existe actuellement aucune cible pour le code XAML ; par conséquent, la chaîne à passer n’est pas définie.  
  
 Vous pouvez également spécifier <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` dans [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` dans [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]), mais en spécifiant <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> est inhabituel car `NotPublic` comme le comportement est déjà la valeur par défaut.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>est le comportement par défaut car il est rare que le code en dehors de l’assembly compilé le code XAML a besoin d’accéder à un élément créé en XAML. Architecture de sécurité WPF avec un comportement de compilation XAML ne sera pas déclarer de champs qui stockent des instances de l’élément en tant que publics, sauf si vous définissez spécifiquement le `x:FieldModifier` pour autoriser l’accès public.  
  
 `x:FieldModifier`est uniquement pertinente pour les éléments avec un [Directive x : Name](../../../docs/framework/xaml-services/x-name-directive.md) , car ce nom est utilisé pour référencer le champ lorsqu’il est public.  
  
 Par défaut, la classe partielle pour l’élément racine est publique ; Toutefois, vous pouvez rendre non publics à l’aide de la [x : ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md). Le [x : ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md) affecte également le niveau d’accès de l’instance de la classe d’élément racine. Vous pouvez placer les deux `x:Name` et `x:FieldModifier` sur la racine de l’élément, mais cela permet uniquement une copie du champ public de l’élément racine, avec le niveau d’accès racine true élément classe toujours contrôlée par [x : ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Voir aussi  
 [XAML et classes personnalisées pour WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Code-behind et XAML dans WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:Name, directive](../../../docs/framework/xaml-services/x-name-directive.md)  
 [Génération d’une application WPF (WPF)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [x:ClassModifier, directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
