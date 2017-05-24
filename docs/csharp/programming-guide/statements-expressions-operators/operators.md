---
title: "Opérateurs (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
caps.latest.revision: 42
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 45f474983747f3b14fac85b8ed00e01fb50853e4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="operators-c-programming-guide"></a>Opérateurs (guide de programmation C#)
En C#, un *opérateur* est un élément de programme qui s'applique à un ou plusieurs *opérandes* dans une expression ou une instruction. Les opérateurs qui prennent un opérande, comme l'opérateur d'incrément (`++`) ou `new`, portent le nom d'opérateurs *unaires* . Les opérateurs qui prennent deux opérandes, comme les opérateurs arithmétiques (`+`,`-`,`*`,`/`) portent le nom d'opérateur *binaires* . Un opérateur, l'opérateur conditionnel (`?:`), prend trois opérandes et est le seul opérateur ternaire en C#.  
  
 L'instruction C# suivante contient un seul opérateur unaire et un seul opérande. L'opérateur d'incrément, `++`, modifie la valeur de l'opérande `y`.  
  
 [!code-cs[csProgGuideStatements#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_1.cs)]  
  
 L'instruction C# suivante contient deux opérateurs binaires, chacun avec deux opérandes. L'opérateur d'assignation, `=`, a la variable de type entier `y` et l'expression `2 + 3` comme opérandes. L'expression `2 + 3` elle-même se compose de l'opérateur Addition et de deux opérandes, `2` et `3`.  
  
 [!code-cs[csProgGuideStatements#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/operators_2.cs)]  
  
## <a name="operators-evaluation-and-operator-precedence"></a>Opérateurs, évaluation et priorité des opérateurs  
 Un opérande peut être une expression valide qui est composée d'une longueur quelconque de code, et qui peut comporter plusieurs sous-expressions. Dans une expression qui contient plusieurs opérateurs, l'ordre dans lequel les opérateurs sont appliqués est déterminé par la *priorité des opérateurs*, *l'associativité*et les parenthèses.  
  
 Chaque opérateur a une priorité définie. Dans une expression qui contient plusieurs opérateurs ayant différents niveaux de priorité, la priorité des opérateurs détermine l'ordre dans lequel les opérateurs sont évalués. Par exemple, l'instruction suivante assigne la valeur 3 à `n1`.  
  
 `n1 = 11 - 2 * 4;`  
  
 La multiplication est effectuée en premier lieu parce que la multiplication est prioritaire sur la soustraction.  
  
 Le tableau suivant répartit les opérateurs en catégories selon le type d'opération qu'ils exécutent. Les catégories sont répertoriées par ordre de priorité.  
  
 **Opérateurs principaux**  
  
|Expression|Description|  
|----------------|-----------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x?.y|Accès au membre<br /><br /> Accès au membre conditionnel.|  
|f[(x)](../../../csharp/language-reference/operators/invocation-operator.md)|Méthode et appel de délégué|  
|a[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> a?[x]|Tableau et accès d'indexeur<br /><br /> Tableau et accès d'indexeur conditionnels|  
|x[++](../../../csharp/language-reference/operators/increment-operator.md)|Post-incrémentation|  
|x[--](../../../csharp/language-reference/operators/decrement-operator.md)|Post-décrémentation|  
|[new](../../../csharp/language-reference/keywords/new-operator.md) T(...)|Création d'objet et de délégué|  
|`new` T(...){...}|Création d'objet avec l'initialiseur. Consultez [Initialiseurs d’objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).|  
|`new` {...}|Initialiseur d'objet anonyme. Consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).|  
|`new` T[...]|Création de tableau. Consultez [Tableaux](../../../csharp/programming-guide/arrays/index.md).|  
|[typeof](../../../csharp/language-reference/keywords/typeof.md)(T)|Obtenir l'objet System.Type pour T|  
|[checked](../../../csharp/language-reference/keywords/checked.md)(x)|Évaluer l'expression dans le contexte vérifié (checked)|  
|[unchecked](../../../csharp/language-reference/keywords/unchecked.md)(x)|Évaluer l'expression dans le contexte non vérifié (unchecked)|  
|[default](../../../csharp/language-reference/keywords/default.md) (T)|Obtenir la valeur par défaut de type T|  
|[delegate](../../../csharp/language-reference/keywords/delegate.md) {}|Fonction anonyme (méthode anonyme)|  
  
 **Opérateurs unaires**  
  
|Expression|Description|  
|----------------|-----------------|  
|[+](../../../csharp/language-reference/operators/addition-operator.md)x|Identité|  
|[-](../../../csharp/language-reference/operators/subtraction-operator.md)x|Négation|  
|[!](../../../csharp/language-reference/operators/logical-negation-operator.md)x|Négation logique|  
|[~](../../../csharp/language-reference/operators/bitwise-complement-operator.md)x|Négation d'opération de bits|  
|[++](../../../csharp/language-reference/operators/increment-operator.md)x|Pré-incrémentation|  
|[--](../../../csharp/language-reference/operators/decrement-operator.md)x|Pré-décrémentation|  
|[(T)](../../../csharp/language-reference/operators/invocation-operator.md)x|Convertir explicitement x en type T|  
  
 **Opérateurs multiplicatifs**  
  
|Expression|Description|  
|----------------|-----------------|  
|[*](../../../csharp/language-reference/operators/multiplication-operator.md)|Multiplication|  
|[/](../../../csharp/language-reference/operators/division-operator.md)|Division|  
|[%](../../../csharp/language-reference/operators/modulus-operator.md)|Reste|  
  
 **Opérateurs additifs**  
  
|Expression|Description|  
|----------------|-----------------|  
|x [+](../../../csharp/language-reference/operators/addition-operator.md) y|Addition, concaténation de chaînes, combinaison de délégués|  
|x [-](../../../csharp/language-reference/operators/subtraction-operator.md) y|Soustraction, suppression de délégué|  
  
 **Opérateurs de décalage**  
  
|Expression|Description|  
|----------------|-----------------|  
|x [<\<](../../../csharp/language-reference/operators/left-shift-operator.md) y|Décalage à gauche|  
|x [>>](../../../csharp/language-reference/operators/right-shift-operator.md) y|Décalage à droite|  
  
 **Opérateurs de type et relationnels**  
  
|Expression|Description|  
|----------------|-----------------|  
|x [\<](../../../csharp/language-reference/operators/less-than-operator.md) y|Inférieur à|  
|x [>](../../../csharp/language-reference/operators/greater-than-operator.md) y|Supérieur à|  
|x [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|Inférieur ou égal à|  
|x [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) y|Supérieur ou égal à|  
|x [is](../../../csharp/language-reference/keywords/is.md) T|Retourne la valeur true si x est de type T, false dans les autres cas|  
|x [as](../../../csharp/language-reference/keywords/as.md) T|Retourne x s'il a le type T ou null si x n'est pas de type T|  
  
 **Opérateurs d’égalité**  
  
|Expression|Description|  
|----------------|-----------------|  
|x [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) y|Égal|  
|x [!=](../../../csharp/language-reference/operators/not-equal-operator.md) y|Différence|  
  
 **Opérateurs logiques, conditionnels et Null**  
  
|Catégorie|Expression|Description|  
|--------------|----------------|-----------------|  
|AND logique|x [&](../../../csharp/language-reference/operators/and-operator.md) y|Opération de bits entière AND, Boolean logique AND|  
|XOR logique|x [^](../../../csharp/language-reference/operators/xor-operator.md) y|Opération de bits entière XOR, Boolean logique XOR|  
|OR logique|x [&#124;](../../../csharp/language-reference/operators/or-operator.md) y|Opération de bits entière OR, Boolean logique OR|  
|AND conditionnel|x [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) y|Évalue y uniquement si x est vrai|  
|OR conditionnel|x [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) y|Évalue y uniquement si x est false|  
|Fusion de Null|x [??](../../../csharp/language-reference/operators/null-conditional-operator.md) o|Prend la valeur y si x est null, sinon prend la valeur x|  
|Conditionnel|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y : z|Prend la valeur de y si x est vrai, de z si x est false|  
  
 **Opérateurs anonymes et d’assignation**  
  
|Expression|Description|  
|----------------|-----------------|  
|[=](../../../csharp/language-reference/operators/assignment-operator.md)|Attribution|  
|x op= y|Assignation composée. Prend en charge ces opérateurs : [+=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [/=](../../../csharp/language-reference/operators/division-assignment-operator.md), [%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [!=](../../../csharp/language-reference/operators/not-equal-operator.md), [<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|  
|(T x) [=>](../../../csharp/language-reference/operators/lambda-operator.md) y|Fonction anonyme (expression lambda)|  
  
## <a name="associativity"></a>l'associativité  
 Lorsque deux opérateurs ou plus, de même niveau de priorité figurent dans une expression, ils sont évalués sur la base de l'associativité. Les opérateurs associatifs sur leur gauche sont évalués dans l'ordre, de gauche à droite. Par exemple, `x * y / z` est évalué comme étant `(x * y) / z`. Les opérateurs associatifs sur leur droite sont évalués dans l'ordre, de droite à gauche. Par exemple, l'opérateur d'assignation est associatif sur sa droite. Dans le cas contraire, le code suivant génère une erreur.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Autre exemple, l’opérateur ternaire ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) est associatif sur sa droite. La plupart des opérateurs binaires sont associatifs sur leur gauche.  
  
 Si les opérateurs présents dans une expression sont associatifs sur leur gauche ou associatifs sur leur droite, les opérandes de chaque expression sont évalués en premier, de gauche à droite. Les exemples suivants illustrent l'ordre d'évaluation des opérateurs et des opérandes.  
  
|Instruction|Ordre d'évaluation|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Ajout de parenthèses  
 Vous pouvez modifier l'ordre imposé par la priorité d'opérateur et l'associativité en utilisant des parenthèses. Par exemple, `2 + 3 * 2` correspond généralement à 8, car les opérateurs de multiplication ont la priorité sur les opérateurs additifs. Toutefois, si vous entrez une expression comme `(2 + 3) * 2`, l'addition est évaluée avant la multiplication, et le résultat est 10. Les exemples suivants illustrent l'ordre d'évaluation dans les expressions entre parenthèses. Comme dans les exemples précédents, l'évaluation des opérandes a lieu avant l'application de l'opérateur.  
  
|Instruction|Ordre d'évaluation|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>Surcharge d'opérateur  
 Vous pouvez modifier le comportement des opérateurs pour les classes et les structs personnalisés. Ce processus est connu sous le nom de *surcharge d'opérateur*. Pour plus d’informations, consultez [Opérateurs surchargeables](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d’informations, consultez [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md) et [Opérateurs C#](../../../csharp/language-reference/operators/index.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Instructions, expressions et opérateurs](../../../csharp/programming-guide/statements-expressions-operators/index.md)

