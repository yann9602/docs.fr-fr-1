---
title: "is (référence C#) | Microsoft Docs"
keywords: "mot clé is (C#), is (C#)"
ms.date: 2017-02-17
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- is_CSharpKeyword
- is
dev_langs:
- CSharp
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c0d300dbb47e64d2425f8af3bc6a819b145786fa
ms.lasthandoff: 03/13/2017

---
# <a name="is-c-reference"></a>is (référence C#) #

Vérifie si un objet est compatible avec un type donné, ou (avec C# 7) teste une expression par rapport à un modèle.

## <a name="testing-for-type-compatibility"></a>Test de compatibilité de type ##

Le mot clé `is` évalue la compatibilité de type au moment de l’exécution. Il détermine si une instance d’objet ou le résultat d’une expression peuvent être convertis en un type spécifié. Sa syntaxe est

```csharp
   expr is type
```

où *expr* est une expression qui correspond à une instance d’un type, et où *type* est le nom du type dans lequel le résultat de *expr* doit être converti. L’instruction `is` est `true` si *expr* est non-Null et si l’objet qui résulte de l’évaluation de l’expression peut être converti en *type* ; sinon, elle retourne `false`.

Par exemple, le code suivant détermine si `obj` peut être casté en une instance de type `Person` :

[!code-cs[is#1](../../../../samples/snippets/csharp/language-reference/keywords/is/is1.cs#1)]

L’instruction `is` a la valeur true si :

- *expr* est une instance du même type que *type*.

- *expr* est une instance d’un type qui dérive de *type*. En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.

- *expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*. Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration. Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.

- *expr* est une instance d’un type qui implémente l’interface *type*.

L’exemple suivant montre que l’expression `is` a la valeur `true` pour chacune de ces conversions.

[!code-cs[is#3](../../../../samples/snippets/csharp/language-reference/keywords/is/is3.cs#3)]

Le mot clé `is` génère un avertissement au moment de la compilation si l’expression est connue pour être toujours soit `true`, soit `false`. Il tient compte uniquement des conversions de référence, des conversions boxing et des conversions unboxing. Il ne tient pas compte des conversions définies par l’utilisateur ni des conversions définies par les opérateurs [implicit](implicit.md) et [explicit](explicit.md) d’un type. L’exemple suivant génère des avertissements, car le résultat de la conversion est connu au moment de la compilation. Notez que l’expression `is` pour les conversions de `int` à `long` et `double` retourne la valeur false, puisque ces conversions sont gérées par l’opérateur [implicit](implicit.md).

[!code-cs[is#2](../../../../samples/snippets/csharp/language-reference/keywords/is/is2.cs#2)]

`expr` peut correspondre à toute expression qui retourne une valeur, à l’exception des méthodes anonymes et des expressions lambda. L’exemple suivant utilise `is` pour évaluer la valeur de retour d’un appel de méthode.   
[!code-cs[is#4](../../../../samples/snippets/csharp/language-reference/keywords/is/is4.cs#4)]

Avec C# 7, vous pouvez utiliser les critères spéciaux avec le [modèle de type](#type) pour écrire du code plus concis qui utilise l’instruction `is`.

## <a name="pattern-matching-with-is"></a>Utilisation des critères spéciaux avec `is` ##

Avec C# 7, les instructions `is` et [switch](../../../csharp/language-reference/keywords/switch.md) prennent en charge les critères spéciaux. Le mot clé `is` prend en charge les modèles suivants :

- [Modèle de type](#type) : permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, caste l’expression en une variable de ce type.

- [Modèle de constante](#constant) : teste si une expression correspond à une valeur de constante spécifiée.

- [Modèle de variable](#var) : correspondance qui réussit toujours et lie la valeur d’une expression à une variable locale. 

### <a name="type" /> Modèle de type </a>

Lorsque vous utilisez le modèle de type pour rechercher des critères spéciaux, `is` permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, effectuer un cast de l’expression en une variable de ce type. Il s’agit d’une extension simple de l’instruction `is` qui permet une évaluation et une conversion de type concises. La forme générale du modèle de type `is` est la suivante :

```csharp
   expr is type varname 
```

où *expr* est une expression qui correspond à une instance d’un type, où *type* est le nom du type dans lequel le résultat de *expr* doit être converti, et où *varname* est l’objet dans lequel le résultat de *expr* est converti si le test `is` a la valeur `true`. 

L’expression `is` est `true` si l’une des affirmations suivantes est vraie :

- *expr* est une instance du même type que *type*.

- *expr* est une instance d’un type qui dérive de *type*. En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.

- *expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*. Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration. Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.

- *expr* est une instance d’un type qui implémente l’interface *type*.

Si *exp* est `true` et si `is` est utilisé avec une instruction `if`, *varname* est assigné et sa portée locale se limite à l’instruction `if`.

L’exemple suivant utilise le modèle de type `is` pour fournir l’implémentation d’une méthode <xref:System.IComparable.CompareTo(System.Object)?displayProperty=fullName> d’un type.

[!code-cs[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Sans critères spéciaux, ce code peut être écrit comme suit. L’utilisation de critères spéciaux de type génère un code lisible plus compact en éliminant la nécessité de tester si le résultat d’une conversion est un `null`.  

[!code-cs[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Le modèle de type `is` génère également du code plus compact lorsqu’il détermine le type d’un type valeur. L’exemple suivant utilise le modèle de type `is` pour déterminer si un objet est une instance `Person` ou `Dog` avant d’afficher la valeur d’une propriété appropriée. 

[!code-cs[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Le code équivalent sans critères spéciaux nécessite une attribution distincte comprenant un cast explicite.

[!code-cs[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="a-nameconstant--constant-pattern"></a><a name="constant" /> Modèle de constante ###

Lorsque vous utilisez des critères spéciaux avec le modèle de constante, `is` teste si une expression est égale à une constante spécifiée. Avec C# 6 et les versions antérieures, le modèle de constante est pris en charge par l’instruction [switch](switch.md). À compter de C# 7, ce modèle est également pris en charge par l’instruction `is`. Sa syntaxe est la suivante :

```csharp
   expr is constant
```

où *expr* est l’expression à évaluer, et où *constant* est la valeur à tester. *constant* peut correspondre à l’une des expressions constantes suivantes : 

- Une valeur littérale

- Le nom d’une variable `const` déclarée

- Une constante d’énumération

L’expression constante est évaluée de la manière suivante :

- Si *expr* et *constant* sont des types intégraux, l’opérateur d’égalité C# détermine si l’expression retourne `true` (autrement dit, si `expr == constant`).

- Sinon, la valeur de l’expression est déterminée par un appel à la méthode statique [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).  

L’exemple suivant combine le modèle de type et le modèle de constante pour tester si un objet est une instance `Dice` et, si c’est le cas, pour déterminer si la valeur obtenue après un lancer de dés est de 6.

[!code-cs[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]
 
### <a name="var" /> Modèle de variable </a>

Une recherche de critères spéciaux qui utilise le modèle de variable réussit toujours. Sa syntaxe est la suivante :

```csharp 
   expr is var varname
```

où la valeur de *expr* est toujours assignée à une variable locale nommée *varname*. *varname* est une variable statique du même type que *expr*. L’exemple suivant utilise le modèle de variable pour assigner une expression à une variable nommée `obj`. Il affiche ensuite la valeur et le type de `obj`.

[!code-cs[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Notez que si *expr* est `null`, l’expression `is` a toujours la valeur true et attribue `null` à *varname*. 

# <a name="c-language-specification"></a>Spécification du langage C#
  
[!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)

