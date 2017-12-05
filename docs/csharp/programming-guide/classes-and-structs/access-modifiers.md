---
title: "Modificateurs d’accès (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# Language, access modifiers
- access modifiers [C#], about
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a567dea6418ff9cfc94c8180a88c872bcf4c96a4
ms.sourcegitcommit: 39b65a49271e082add68cb737b48fdbe09d24718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2017
---
# <a name="access-modifiers-c-programming-guide"></a>Modificateurs d’accès (Guide de programmation C#)
Tous les types et membres de type ont un niveau d’accessibilité, qui détermine s’ils peuvent être utilisés à partir d’un autre code de votre assembly ou d’autres assemblys. Utilisez les modificateurs d’accès suivants pour spécifier l’accessibilité d’un type ou d’un membre au moment où vous le déclarez :  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre. 
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Seul du code de la même classe ou du même struct peut accéder au type ou au membre.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Seul du code de la même classe, ou du code d’une classe dérivée de cette classe, peut accéder au type ou au membre.  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.  
  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) Tout code de l’assembly dans lequel le type ou le membre est déclaré, ou d’une classe dérivée dans un autre assembly, peut accéder au type ou au membre. 

 [private protected](../../../csharp/language-reference/keywords/private-protected.md) Seul du code de la même classe ou dans un type dérivé de cette classe peut accéder au type ou au membre au sein de son assembly de déclaration.
  
 Les exemples suivants montrent comment spécifier des modificateurs d’accès sur un type et un membre :  
  
 [!code-csharp[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Les modificateurs d’accès ne peuvent pas tous être utilisés par tous les types ou membres dans tous les contextes. De plus, dans certains cas, l’accessibilité d’un membre de type est limitée par l’accessibilité de son type conteneur. Les sections suivantes fournissent plus de détails sur l’accessibilité.  
  
## <a name="class-and-struct-accessibility"></a>Accessibilité des classes et des structs  
 Les classes et les structs qui sont déclarés directement dans un espace de noms (autrement dit, qui ne sont pas imbriqués dans d’autres classes ou structs) peuvent être déclarés comme public ou internal. Le niveau d’accès par défaut est internal si aucun modificateur d’accès n’est spécifié.  
  
 Les membres de struct, y compris les classes et structs imbriqués, peuvent être déclarés comme public, internal ou private. Les membres de classe, notamment les classes et structs imbriqués, peuvent être public, protected internal, protected, internal, private protected ou private. Le niveau d’accès pour les membres de classe et de struct, y compris les classes et structs imbriqués, est private par défaut. L’accès aux types imbriqués private n’est pas possible hors du type conteneur.  
  
 Les classes dérivées ne peuvent pas avoir une accessibilité supérieure à celle de leurs types de base. Vous ne pouvez donc pas avoir une classe public `B` qui dérive d’une classe internal `A`. Si cela était autorisé, cela aurait pour effet de rendre `A` public, car tous les membres protected ou internal de `A` seraient accessibles à partir de la classe dérivée.  
  
 Vous pouvez utiliser InternalsVisibleToAttribute pour autoriser d’autres assemblys spécifiques à accéder à vos types internal. Pour plus d’informations, consultez [Assemblys friend](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
## <a name="class-and-struct-member-accessibility"></a>Accessibilité des membres de classe et de struct  
 Vous pouvez déclarer les membres de classe (notamment les classes et structs imbriqués) avec l’un des six types d’accès. Les membres de struct ne peuvent pas être déclarés comme protected, car les structs ne prennent pas en charge l’héritage.  
  
 Normalement, l’accessibilité d’un membre ne peut pas être supérieure à l’accessibilité du type qui le contient. Toutefois, un membre public d’une classe internal est accessible hors de l’assembly si le membre implémente des méthodes d’interface ou substitue des méthodes virtuelles qui sont définies dans une classe de base public.  
  
 Le type d’un membre qui est un champ, une propriété ou un événement doit être au moins aussi accessible que le membre lui-même. De la même façon, le type de retour et les types de paramètres d’un membre qui est une méthode, un indexeur ou un délégué doivent être au moins aussi accessibles que le membre lui-même. Par exemple, vous ne pouvez pas avoir une méthode public `M` qui retourne une classe `C`, sauf si `C` est également public. Vous ne pouvez pas non plus avoir une propriété protected de type `A` si `A` est déclaré comme private.  
  
 Les opérateurs définis par l’utilisateur doivent toujours être déclarés comme public. Pour plus d’informations, consultez [operator (référence C#)](../../../csharp/language-reference/keywords/operator.md).  
  
 Les finaliseurs ne peuvent pas avoir de modificateurs d’accessibilité.  
  
 Pour définir le niveau d’accès pour un membre de classe ou de struct, ajoutez le mot clé approprié à la déclaration du membre, comme illustré dans l’exemple suivant.  
  
 [!code-csharp[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Le niveau d’accessibilité protected internal signifie protected OU internal, et non protected ET internal. Cela signifie qu’un membre protected internal est accessible à partir de n’importe quelle classe dans le même assembly, y compris des classes dérivées. Pour limiter l’accessibilité uniquement aux classes dérivées du même assembly, déclarez la classe de base comme internal et ses membres comme protected. De plus, à compter de C# 7.2, vous pouvez utiliser le modificateur d’accès private protected pour obtenir le même résultat sans déclarer la classe conteneur comme internal.  
  
## <a name="other-types"></a>Autres types  
 Les interfaces qui sont déclarées directement dans un espace de noms peuvent être déclarées comme public ou internal et, comme les classes et les structs, les interfaces ont le niveau d’accès internal par défaut. Les membres d’interface sont toujours public, car une interface est censée permettre à d’autres types d’accéder à une classe ou un struct. Il n’est pas possible d’appliquer des modificateurs d’accès aux membres d’interface.  
  
 Les membres d’énumération sont toujours public, et aucun modificateur d’accès ne peut leur être appliqué.  
  
 Les délégués se comportent comme des classes et des structs. Par défaut, ils ont un accès internal quand ils sont déclarés directement dans un espace de noms, et un accès private quand ils sont imbriqués.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [protected internal](../../../csharp/language-reference/keywords/protected-internal.md)  
 [private protected](../../../csharp/language-reference/keywords/private-protected.md)  
 [class](../../../csharp/language-reference/keywords/class.md)  
 [struct](../../../csharp/language-reference/keywords/struct.md)  
 [interface](../../../csharp/language-reference/keywords/interface.md)
