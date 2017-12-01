---
title: "Niveaux d’accessibilité (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a>Niveaux d’accessibilité (référence C#)
Utilisez les modificateurs d’accès [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md) pour spécifier l’un des niveaux d’accessibilité déclarée ci-dessous pour les membres.  
  
|Accessibilité déclarée|Signification|  
|----------------------------|-------------|  
|`public`|L’accès n’est pas limité.|  
|`protected`|L’accès est limité à la classe conteneur ou aux types dérivés de la classe conteneur.|  
|`internal`|L’accès est limité à l’assembly actuel.|  
|`protected internal`|L’accès est limité à l’assembly actuel ou aux types dérivés de la classe conteneur.|  
|`private`|L’accès est limité au type conteneur.|  
|`private protected`|L’accès est limité à la classe de conteneur ou les types dérivés de la classe de conteneur dans l’assembly actuel.|  
  
 Modificateur d’accès qu’une seule est autorisé pour un membre ou un type, sauf lorsque vous utilisez la `protected internal` ou `private protected` combinaisons.  
  
 Les modificateurs d’accès ne sont pas autorisés sur les espaces de noms. Les espaces de noms ne présentent aucune limitation d’accès.  
  
 Selon le contexte dans lequel une déclaration de membre est effectuée, seules certaines accessibilités déclarées sont autorisées. Si aucun modificateur d’accès n’est spécifié dans une déclaration de membre, une accessibilité par défaut est utilisée.  
  
 Les types de premier niveau, qui ne sont pas imbriqués dans d’autres types, peuvent uniquement avoir une accessibilité `internal` ou `public`. L’accessibilité par défaut de ces types est `internal`.  
  
 Les types imbriqués, qui sont membres d’autres types, peuvent avoir les accessibilités déclarées indiquées dans le tableau suivant.  
  
|Membres de|Accessibilité par défaut du membre|Accessibilité déclarée du membre autorisée|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|Aucune|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|Aucune|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 L’accessibilité d’un type imbriqué dépend de son [domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md), qui est déterminé à la fois par l’accessibilité déclarée du membre et par le domaine d’accessibilité du type conteneur immédiat. Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [Limitations sur l’utilisation des niveaux d’accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
