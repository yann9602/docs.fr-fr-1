---
title: "Restriction d’accessibilité de l’accesseur (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 347fffa4f612c5cb674a6529e46c0b1785670c95
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a>Restriction d’accessibilité de l’accesseur (Guide de programmation C#)
Les parties [get](../../../csharp/language-reference/keywords/get.md) et [set](../../../csharp/language-reference/keywords/set.md) d’une propriété ou d’un indexeur sont appelées *accesseurs*. Par défaut, ces accesseurs ont la même visibilité, ou niveau d’accès : celle de la propriété ou de l’indexeur auquel ils appartiennent. Pour plus d’informations, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md). Toutefois, il peut parfois s’avérer utile de restreindre l’accès à l’un de ces accesseurs. En général, cela implique de restreindre l’accessibilité de l’accesseur `set`, tout en gardant l’accesseur `get` publiquement accessible. Exemple :  
  
 [!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 Dans cet exemple, une propriété appelée `Name` définit un accesseur `get` et `set`. L’accesseur `get` reçoit le niveau d’accessibilité de la propriété elle-même, `public` dans le cas présent, alors que l’accesseur `set` est restreint explicitement par l’application du modificateur d’accès [protected](../../../csharp/language-reference/keywords/protected.md) à l’accesseur lui-même.  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a>Restrictions sur les modificateurs d’accès sur les accesseurs  
 L’utilisation de modificateurs d’accesseurs sur les propriétés ou les indexeurs est soumise aux conditions suivantes :  
  
-   Vous ne pouvez pas utiliser de modificateurs d’accesseur sur une interface ou sur une implémentation de membre d’[interface](../../../csharp/language-reference/keywords/interface.md) explicite.  
  
-   Vous pouvez utiliser les modificateurs d’accesseur uniquement si la propriété ou l’indexeur dispose à la fois d’accesseurs `set` et `get`. Dans ce cas, le modificateur est autorisé uniquement sur l’un des deux accesseurs.  
  
-   Si la propriété ou l’indexeur possède un modificateur [override](../../../csharp/language-reference/keywords/override.md), le modificateur d’accesseur doit correspondre à l’accesseur de l’accesseur substitué, le cas échant.  
  
-   Le niveau d’accessibilité sur l’accesseur doit être plus restrictif que le niveau d’accessibilité sur la propriété ou l’indexeur eux-mêmes.  
  
## <a name="access-modifiers-on-overriding-accessors"></a>Modificateurs d’accès sur les accesseurs de substitution  
 Quand vous substituez une propriété ou un indexeur, les accesseurs remplacés doivent être accessibles au code de substitution. Par ailleurs, le niveau d’accessibilité à la fois de la propriété et de l’indexeur, ainsi que celui des accesseurs doivent correspondre à la propriété/l’indexeur et aux accesseurs substitués correspondants. Exemple :  
  
 [!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a>Implémentation des interfaces  
 Quand vous utilisez un accesseur pour implémenter une interface, l’accesseur peut ne pas avoir de modificateur d’accès. Toutefois, si vous implémentez l’interface à l’aide d’un accesseur, tel que `get`, l’autre accesseur peut avoir un modificateur d’accès, comme dans l’exemple suivant :  
  
 [!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a>Domaine d’accessibilité de l’accesseur  
 Si vous utilisez un modificateur d’accès sur l’accesseur, le [domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md) de l’accesseur est déterminé par ce modificateur.  
  
 Si vous n’avez pas utilisé un modificateur d’accès sur l’accesseur, le domaine d’accessibilité de l’accesseur est déterminé par le niveau d’accessibilité de la propriété ou de l’indexeur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient trois classes, `BaseClass`, `DerivedClass` et `MainClass`. Il y a deux propriétés sur `BaseClass`, `Name` et `Id` sur les deux classes. L’exemple montre comment la propriété `Id` sur `DerivedClass` peut être masquée par la propriété `Id` sur `BaseClass` quand vous utilisez un modificateur d’accès restrictif tel que [protected](../../../csharp/language-reference/keywords/protected.md) ou [private](../../../csharp/language-reference/keywords/private.md). Par conséquent, quand vous affectez des valeurs à cette propriété, la propriété sur la classe `BaseClass` est appelée à la place. Le remplacement du modificateur d’accès par [public](../../../csharp/language-reference/keywords/public.md) rend la propriété accessible.  
  
 L’exemple montre également qu’un modificateur d’accès restrictif, tel que `private` ou `protected`, sur l’accesseur `set` de la propriété `Name` dans `DerivedClass` empêche l’accès à l’accesseur et génère une erreur quand vous lui affectez une valeur.  
  
 [!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a>Commentaires  
 Notez que si vous remplacez la déclaration `new private string Id` par `new public string Id`, vous obtenez la sortie suivante :  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)

