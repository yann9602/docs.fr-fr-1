---
title: "Opérateurs C#"
ms.date: 2017-03-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.operators
dev_langs:
- CSharp
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
caps.latest.revision: 40
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
ms.sourcegitcommit: 0dc2fcee3903b80816c98bab47e2b9a2e5ef78b0
ms.openlocfilehash: 2ec2f07dda8979ca6def0648aae1ef23a8df6369
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="c-operators"></a>Opérateurs C#
C# fournit de nombreux opérateurs, qui sont des symboles spécifiant quelles opérations (mathématiques, indexation, appel de fonction, etc.) effectuer dans une expression.  Vous pouvez [surcharger](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) de nombreux opérateurs pour modifier leur signification quand ils sont appliqués à un type défini par l’utilisateur.  
  
 Les opérations sur les types intégraux (comme `==`, `!=`, `<`, `>`, `&` ou `|`) sont en général autorisées sur les types énumération (`enum`).  
  
 Les sections répertorient les opérateurs C# de la priorité la plus élevée à la plus basse.  Les opérateurs inclus dans chaque section partagent le même niveau de priorité.  
  
## <a name="primary-operators"></a>Opérateurs principaux  
 Ce sont les opérateurs dont la priorité est la plus élevée.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) : accès au membre.  
  
 [x?.y](../../../csharp/language-reference/operators/null-conditional-operators.md) : accès au membre conditionnel Null.  Retourne `null` si l’opérande de gauche a la valeur `null`.  
 
 [x?[y]](../../../csharp/language-reference/operators/null-conditional-operators.md) : accès à l’index conditionnel Null. Retourne `null` si l’opérande de gauche a la valeur `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) : appel de fonction.  
  
 [a&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md) : indexation de l’objet d’agrégation.  
   
 [x++](../../../csharp/language-reference/operators/increment-operator.md) : incrément suffixé.  Retourne la valeur de x et met à jour l'emplacement de stockage avec la valeur de x augmentée de un (ajoute généralement l'entier 1).  
  
 [x--](../../../csharp/language-reference/operators/decrement-operator.md) : décrément suffixé.  Retourne la valeur de x et met à jour l'emplacement de stockage avec la valeur de x diminuée de un (soustrait généralement l'entier 1).  
  
 [new](../../../csharp/language-reference/keywords/new-operator.md) : instanciation de type.  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) : retourne l’objet System.Type qui représente l’opérande.  
  
 [checked](../../../csharp/language-reference/keywords/checked.md) : active le contrôle de dépassement de capacité pour les opérations sur les entiers.  
  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) : désactive le contrôle de dépassement de capacité pour les opérations sur les entiers.  Il s'agit du comportement de compilateur par défaut.  
  
 [default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) : retourne la valeur par défaut de type T, la valeur `null` pour les types de référence, zéro pour les types numériques et zéro/`null` renseigné dans les membres pour les types struct.  
  
 [delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) : déclare et retourne une instance de délégué.  
  
 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) : retourne la taille en octets de l’opérande du type.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md) : déréférencement de pointeur associé à l’accès au membre.  
  
## <a name="unary-operators"></a>Opérateurs unaires  
 Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [+x](../../../csharp/language-reference/operators/addition-operator.md) : retourne la valeur de x.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) : négation numérique.  
  
 [!x](../../../csharp/language-reference/operators/logical-negation-operator.md) : négation logique.  
  
 [~x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) : complément au niveau du bit.  
  
 [++x](../../../csharp/language-reference/operators/increment-operator.md) : incrément préfixé.  Retourne la valeur de x après avoir mis à jour l'emplacement de stockage avec la valeur de x augmentée de un (ajoute généralement l'entier 1).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) : décrément préfixé.  Retourne la valeur de x après avoir mis à jour l'emplacement de stockage avec la valeur de x diminuée de un (ajoute généralement l'entier 1).  
  
 [(T)x](../../../csharp/language-reference/operators/invocation-operator.md) : cast de type.  
  
 [await](../../../csharp/language-reference/keywords/await.md) : attend un `Task`.  
  
 [&x](../../../csharp/language-reference/operators/and-operator.md) : adresse de.  
  
 [*x](../../../csharp/language-reference/operators/multiplication-operator.md) : déréférencement.  
  
## <a name="multiplicative-operators"></a>Opérateurs multiplicatifs  
 Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) : multiplication.  
  
 [x / y](../../../csharp/language-reference/operators/division-operator.md) : division.  Si les opérandes sont des entiers, le résultat est un entier tronqué vers zéro (par exemple, `-7 / 2 is -3`).  
  
 [x % y](../../../csharp/language-reference/operators/modulus-operator.md) : modulo.  Si les opérandes sont des entiers, cet opérateur renvoie le reste de la division de x par y.  Si `q = x / y` et `r = x % y`, alors `x = q * y + r`.  
  
## <a name="additive-operators"></a>Opérateurs additifs  
 Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [x + y](../../../csharp/language-reference/operators/addition-operator.md) : addition.  
  
 [x – y](../../../csharp/language-reference/operators/subtraction-operator.md) : soustraction.  
  
## <a name="shift-operators"></a>Opérateurs de décalage  
 Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [x <\<  y](../../../csharp/language-reference/operators/left-shift-operator.md) : décalage des bits vers la gauche et remplissage avec zéro à droite.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) : décalage des bits vers la droite.  Si l'opérande de gauche est `int` ou `long`, alors les bits de gauche sont remplis avec le bit de signe.  Si l'opérande de gauche est `uint` ou `ulong`, alors les bits de gauche sont remplis avec zéro.  
  
## <a name="relational-and-type-testing-operators"></a>Opérateurs relationnels et de test de type  
 Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) : inférieur à (true si x est inférieur à y).  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) : supérieur à (true si x est supérieur à y).  
  
 [x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) : supérieur ou égal à.  
  
 [x >= y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) : supérieur ou égal à.  
  
 [is](../../../csharp/language-reference/keywords/is.md) : compatibilité du type.  Retourne true si l’opérande de gauche évalué peut être converti en type spécifié dans l’opérande de droite (type statique).  
  
 [as](../../../csharp/language-reference/keywords/as.md) : conversion de type.  Retourne l'opérande de gauche converti en type spécifié par l'opérande de droite (type statique), mais `as` retourne `null` où `(T)x` lèverait une exception.  
  
## <a name="equality-operators"></a>Opérateurs d'égalité  
 Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) : égalité.  Par défaut, pour les types de référence autres que `string`, cet opérateur retourne l'égalité de référence (test d'identité).  Toutefois, des types peuvent surcharger `==`, donc si votre objectif est de tester l'identité, il est préférable d'utiliser la méthode `ReferenceEquals` sur `object`.  
  
 [x != y](../../../csharp/language-reference/operators/not-equal-operator.md) : différent.  Consultez le commentaire sur `==`.  Si un type surcharge `==`, alors il doit surcharger `!=`.  
  
## <a name="logical-and-operator"></a>Opérateur AND logique  
 Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur l'opérateur à accéder à la page détaillée assortie d'exemples.  
  
 [x & y](../../../csharp/language-reference/operators/and-operator.md) : ET logique ou au niveau du bit.  L'utilisation avec des types entiers et des types `enum` est généralement autorisée.  
  
## <a name="logical-xor-operator"></a>Opérateur XOR logique  
 Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur l'opérateur à accéder à la page détaillée assortie d'exemples.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) : XOR logique ou au niveau du bit.  Vous pouvez l'utiliser généralement avec des types entiers et des types `enum`.  
  
## <a name="logical-or-operator"></a>Opérateur OR logique  
 Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur l'opérateur à accéder à la page détaillée assortie d'exemples.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) : OU logique ou au niveau du bit.  L'utilisation avec des types entiers et des types `enum` est généralement autorisée.  
  
## <a name="conditional-and-operator"></a>Opérateur AND conditionnel  
 Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur l'opérateur à accéder à la page détaillée assortie d'exemples.  
  
 [x && y](../../../csharp/language-reference/operators/conditional-and-operator.md) : ET logique.  Si le premier opérande a la valeur false, alors C# n’évalue pas le second opérande.  
  
## <a name="conditional-or-operator"></a>Opérateur OR conditionnel  
 Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur l'opérateur à accéder à la page détaillée assortie d'exemples.  
  
 [x &#124;&#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) : OU logique.  Si le premier opérande a la valeur true, alors C# n’évalue pas le second opérande.  
  
## <a name="null-coalescing-operator"></a>Opérateur de fusion de Null  
 Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur l'opérateur à accéder à la page détaillée assortie d'exemples.  
  
 [x ?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) : retourne `x` si non `null` ; dans le cas contraire, retourne `y`.  
  
## <a name="conditional-operator"></a>Opérateur conditionnel  
 Cet opérateur a une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur l'opérateur à accéder à la page détaillée assortie d'exemples.  
  
 [t ? x : y](../../../csharp/language-reference/operators/conditional-operator.md) : si le test `t` a la valeur true, alors évalue et retourne `x` ; sinon, évalue et retourne `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Opérateurs d'assignation et lambda  
 Ces opérateurs ont une priorité supérieure à celle de la section suivante et une priorité inférieure à celle de la section précédente.  Notez que vous pouvez cliquer sur les opérateurs pour accéder aux pages détaillées assorties d'exemples.  
  
 [x = y](../../../csharp/language-reference/operators/assignment-operator.md) : affectation.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) : incrément.  Additionne la valeur de `y` à la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.  Si `x` désigne un `event`, alors `y` doit être une fonction appropriée que C# ajoute en tant que gestionnaire d'événements.  
  
 [x -= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) : décrément.  Soustrait la valeur de `y` de la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.  Si `x` désigne un `event`, alors `y` doit être une fonction appropriée que C# supprime en tant que gestionnaire d'événements.  
  
 [x *= y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) : affectation de multiplication.  Multiplie la valeur de `y` par la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.  
  
 [x /= y](../../../csharp/language-reference/operators/division-assignment-operator.md) : affectation de division.  Divise la valeur de `x` par la valeur de `y`, stocke le résultat dans `x` et retourne la nouvelle valeur.  
  
 [x %= y](../../../csharp/language-reference/operators/modulus-assignment-operator.md) : affectation de modulo.  Divise la valeur de `x` par la valeur de `y`, stocke le reste dans `x` et retourne la nouvelle valeur.  
  
 [x &= y](../../../csharp/language-reference/operators/and-assignment-operator.md) : affectation ET.  Assigne l'opérateur AND à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.  
  
 [x &#124;= y](../../../csharp/language-reference/operators/or-assignment-operator.md) : affectation OU.  Assigne l'opérateur OR à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.  
  
 [x ^= y](../../../csharp/language-reference/operators/xor-assignment-operator.md) : affectation XOR.  Assigne l'opérateur XOR à la valeur de `y` et la valeur de `x`, stocke le résultat dans `x` et retourne la nouvelle valeur.  
  
 [x <<= y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) : affectation de décalage vers la gauche.  Décale la valeur de `x` vers la gauche de `y` places, stocke le résultat dans `x` et retourne la nouvelle valeur.  
  
 [x >>= y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) : affectation de décalage vers la droite.  Décale la valeur de `x` vers la droite de `y` places, stocke le résultat dans `x` et retourne la nouvelle valeur.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md) : déclaration lambda.  
  
## <a name="arithmetic-overflow"></a>Dépassement arithmétique  
 Les opérateurs arithmétiques ([+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [*](../../../csharp/language-reference/operators/multiplication-operator.md) et [/](../../../csharp/language-reference/operators/division-operator.md)) peuvent produire des résultats qui sont en dehors de la plage de valeurs possibles pour le type numérique concerné. Reportez-vous à la section d'un opérateur particulier pour obtenir plus d'informations, mais en règle générale, les points suivants s'appliquent :  
  
- Le dépassement arithmétique d'un entier lève soit une exception <xref:System.OverflowException> ou ignore les bits les plus significatifs du résultat. La division d'un entier par zéro lève toujours une exception @System.DivideByZeroException.  

   En cas de dépassement d’un entier, ce qui se produit dépend du contexte d’exécution, lequel peut être [checked ou unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md). Dans un contexte checked, une exception <xref:System.OverflowException> est levée. Dans un contexte unchecked, les bits les plus significatifs du résultat sont ignorés et l'exécution se poursuit. Ainsi, C# vous donne la possibilité de traiter ou d'ignorer le dépassement. Par défaut, les opérations arithmétiques se produisent dans un contexte *unchecked*. 

   En plus des opérations arithmétiques, des casts entre types intégraux peuvent générer un dépassement (par exemple en cas de conversion de type de [long](../../../csharp/language-reference/keywords/long.md) en [int](../../../csharp/language-reference/keywords/int.md)). Ils sont sujets à une exécution checked ou unchecked. En revanche, les opérateurs de bits et les opérateurs de décalage ne génèrent jamais de dépassement.  
   
-   Le dépassement arithmétique ou la division par zéro d'une virgule flottante ne lèvent jamais d'exception, car les types à virgule flottante se basent sur IEEE 754 et peuvent représenter l'infini et NaN (n'est pas un nombre).  
  
-   Le dépassement arithmétique d’un nombre [décimal](../../../csharp/language-reference/keywords/decimal.md) lève toujours une exception <xref:System.OverflowException>. La division d'un nombre décimal par zéro lève toujours une exception <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [C#](../../../csharp/csharp.md)   
 [Opérateurs surchargeables](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)

