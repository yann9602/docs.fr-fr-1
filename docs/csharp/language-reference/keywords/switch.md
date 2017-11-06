---
title: "switch, mot clé (référence C#)"
ms.date: 03/07/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: "47"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66528c9804b74b0bba088627b3116be804c65eb0
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="switch-c-reference"></a>switch (référence C#)
`switch` est une instruction de sélection qui choisit une *section de commutation* unique à exécuter à partir d’une liste de candidats en fonction d’une mise en correspondance de modèle avec l’*expression de correspondance*. 
  
 [!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]  

L’instruction `switch` est souvent utilisée comme alternative à une construction [if-else](if-else.md) si une expression unique est testée en fonction de trois conditions ou plus. Par exemple, l’instruction `switch` suivante détermine laquelle des trois valeurs possibles a été affectée à une variable de type `Color` : 

[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)] 

Il est équivalent à l’exemple suivant qui utilise une construction `if` -`else`. 

[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)] 

## <a name="the-match-expression"></a>Expression de correspondance

L’expression de correspondance fournit la valeur à mettre en correspondance avec les modèles dans les étiquettes `case`. Sa syntaxe est la suivante :

```csharp
   switch (expr)
```

En C# 6, l’expression de correspondance doit être une expression qui retourne une valeur d’un des types suivants :

- [char](char.md),
- [string](string.md),
- [bool](bool.md), 
- valeur intégrale, telle que [int](int.md) ou [long](long.md),
- ou valeur [enum](enum.md).

À compter de C# 7, l’expression de correspondance peut être toute expression non Null.
 
## <a name="the-switch-section"></a>Section de commutation
 
 Une instruction `switch` inclut une ou plusieurs sections de commutation. Chaque section de commutation contient une ou plusieurs *étiquettes case* suivies d’une ou de plusieurs instructions. L'exemple suivant montre une instruction `switch` simple qui a trois sections switch. Chaque section switch a un nom de cas, tel que `case 1:` et une liste de deux instructions.
 
  Une instruction `switch` peut inclure un nombre quelconque de sections de commutation, et chaque section peut contenir une ou plusieurs étiquettes case, comme dans l’exemple ci-dessous. Toutefois, deux étiquettes case ne doivent pas contenir la même expression.  

 [!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]  

 Une seule section de commutation s’exécute dans une instruction switch. C# ne permet pas à l’exécution de passer d’une section switch à la suivante. Pour cette raison, le code suivant génère une erreur du compilateur, CS0163 : « Le contrôle ne peut pas passer d’une étiquette case (<case label>) à une autre ».   

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
Si cela est nécessaire, il est possible de procéder en quittant explicitement la section de commutation à l’aide d’une instruction [break](break.md), [goto](goto.md) ou [return](return.md). Toutefois, le code suivant est également valide, car il garantit que le contrôle du programme ne peut pas passer à la section de commutation `default`.
  
 [!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]    
  
 L’exécution de la liste d’instructions dans la section de commutation avec une étiquette case qui correspond à l’expression de correspondance commence avec la première instruction et continue en suivant la liste d’instructions, en général jusqu’à ce qu’une instruction de saut, telle que `break`, `goto case`, `goto label`, `return` ou `throw`, soit atteinte. À ce stade, le contrôle est transféré hors de l'instruction `switch` ou vers un autre nom de cas. Si une instruction `goto` est utilisée, elle doit transférer le contrôle à une étiquette constante. Cette restriction est nécessaire, car tenter de transférer le contrôle à une étiquette non constante peut avoir des effets indésirables, tels que le transfert du contrôle à un emplacement inattendu dans le code ou la création d’une boucle sans fin.

## <a name="case-labels"></a>Étiquettes case

 Chaque étiquette case spécifie un modèle à comparer à l’expression de correspondance (la variable `caseSwitch` dans les exemples précédents). S’ils correspondent, le contrôle est transféré à la section de commutation qui contient la **première** étiquette case correspondante. Si aucun modèle d’étiquette case ne correspond à l’expression de correspondance, le contrôle est transféré à la section avec l’étiquette case `default`, si une telle section existe. En l’absence d’étiquette case `default`, aucune instruction d’aucune section de commutation n’est exécutée et le contrôle est transféré hors de l’instruction `switch`.

 Pour plus d’informations sur l’instruction `switch` et les critères spéciaux, consultez la section [Critères spéciaux avec l’instruction `switch`](#pattern).

 Étant donné que C# 6 prend en charge uniquement le modèle de constante et n’autorise pas la répétition des valeurs constantes, les étiquettes case définissent des valeurs qui s’excluent mutuellement, et un seul modèle peut correspondre à l’expression de correspondance. Par conséquent, l’ordre dans lequel les instructions `case` apparaissent n’a pas d’importance.

 Dans C# 7, toutefois, comme d’autres modèles sont pris en charge, les étiquettes case ne sont pas tenues de définir des valeurs s’excluant mutuellement et plusieurs modèles peuvent correspondre à l’expression de correspondance. Comme seules les instructions de la section de commutation contenant le premier modèle correspondant sont exécutées, l’ordre dans lequel les instructions `case` apparaissent est désormais important. Si C# détecte une section de commutation dont la ou les instructions case sont équivalentes aux instructions précédentes, ou en sont des sous-ensembles, C# génère une erreur du compilateur, CS8120, « Le switch case a déjà été pris en charge par un case antérieur ». 

 L’exemple suivant illustre une instruction `switch` qui utilise divers modèles ne s’excluant pas mutuellement. Si vous déplacez la section de commutation `case 0:` pour qu’elle ne soit plus la première section dans l’instruction `switch`, C# génère une erreur du compilateur, car un entier dont la valeur est égale à zéro est un sous-ensemble de tous les entiers, ce qui est le modèle défini par l’instruction `case int val`.

 [!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]    

Vous pouvez corriger ce problème et éliminer l’avertissement du compilateur de deux façons :

- en modifiant l’ordre des sections de commutation ; 
 
- en utilisant une clause </a name="when">when</a> dans l’étiquette `case`.
 
## <a name="the-default-case"></a>Étiquette case `default`

L’étiquette case `default` spécifie la section de commutation à exécuter si l’expression de correspondance ne correspond à aucune autre étiquette `case`. En l’absence d’une étiquette case `default`, si l’expression de correspondance ne correspond à aucune autre étiquette `case`, le flux de programme traverse l’instruction `switch`.

L’étiquette case `default` peut apparaître à n’importe quelle position dans l’instruction `switch`. Quelle que soit sa position dans le code source, elle est toujours évaluée en dernier, une fois que toutes les étiquettes `case` ont été évaluées.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> Critères spéciaux avec l’instruction `switch`
  
Chaque instruction `case` définit un modèle qui, s’il correspond à l’expression de correspondance, entraîne l’exécution de la section de commutation qui le contient. Toutes les versions de C# prennent en charge le modèle de constante. Les autres modèles sont pris en charge à compter de C# 7. 
  
### <a name="constant-pattern"></a>Modèle de constante 

Le modèle de constante teste si l’expression de correspondance est égale à une constante spécifiée. Sa syntaxe est la suivante :

```csharp
   case constant:
```

où *constant* est la valeur à tester. *constant* peut être l’une quelconque des expressions constantes suivantes : 

- Un littéral de [valeur booléenne](bool.md), `true` ou `false`
- Toute constante intégrale, de type [int](int.md), [long](long.md) ou [byte](byte.md) 
- Le nom d’une variable `const` déclarée
- Une constante d’énumération
- Un littéral de type [char](char.md)
- Un littéral de type [string](string.md)

L’expression constante est évaluée de la manière suivante :

- Si *expr* et *constant* sont des types intégraux, l’opérateur d’égalité C# détermine si l’expression retourne `true` (autrement dit, si `expr == constant`).

- Sinon, la valeur de l’expression est déterminée par un appel à la méthode statique [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).  

L’exemple suivant utilise le modèle de constante pour déterminer si une date particulière correspond à un jour de week-end, au premier jour de la semaine, au dernier jour de la semaine de travail ou au milieu de la semaine de travail. Il évalue la propriété <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> du jour actuel par rapport aux membres de l’énumération <xref:System.DayOfWeek>. 

[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

L’exemple suivant utilise le modèle de constante pour gérer l’entrée d’utilisateur dans une application console qui simule une machine à café automatique.
  
 [!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]  

### <a name="type-pattern"></a>Modèle de type

Le modèle de type permet une évaluation et une conversion rapides de type. Lorsqu’il est utilisé avec l’instruction `switch` pour effectuer une mise en correspondance de modèle, il permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, il effectue un cast de l’expression en une variable de ce type. Sa syntaxe est la suivante :

```csharp
   case type varname 
```
où *type* est le nom du type vers lequel le résultat de *expr* doit être converti, et *varname* est l’objet vers lequel le résultat de *expr* est converti si la correspondance est établie. 

L’expression `case` est `true` si l’une quelconque des affirmations suivantes est vraie :

- *expr* est une instance du même type que *type*.

- *expr* est une instance d’un type qui dérive de *type*. En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.

- *expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*. Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration de type. Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.

- *expr* est une instance d’un type qui implémente l’interface *type*.

Si l’expression case est true, *varname* est définitivement assigné et a une portée locale au sein de la section de commutation uniquement.

Notez que `null` ne correspond pas à un type. Pour mettre en correspondance `null`, vous utilisez l’étiquette `case` suivante :

```csharp
case null:
```
 
L’exemple suivant utilise le modèle de type pour fournir des informations sur différentes sortes de types de collection.

[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Sans critères spéciaux, ce code peut être écrit comme suit. L’utilisation de critères spéciaux de type génère un code plus compact et lisible en éliminant la nécessité de tester si le résultat d’une conversion est un `null` et d’effectuer des casts répétés.  

[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>Instruction `case` et clause `when`

À compter de C# 7, comme les instructions case ne s’excluent pas nécessairement mutuellement, vous pouvez ajouter une clause `when` pour spécifier une condition supplémentaire qui doit être satisfaite pour que l’instruction case soit évaluée à true. La clause `when` peut être toute expression qui retourne une valeur booléenne. Le plus souvent, la clause `when` est utilisée pour empêcher l’exécution d’une section de commutation quand la valeur d’une expression de correspondance est `null`. 

 L’exemple suivant définit une classe `Shape` de base, une classe `Rectangle` qui dérive de `Shape` et une classe `Square` qui dérive de `Rectangle`. Il utilise la clause `when` pour garantir que le `ShowShapeInfo` traite un objet `Rectangle` qui s’est vu assigner des longueurs et des largeurs égales comme celles d’un objet `Square` même s’il n’a pas été instancié comme objet `Square`. La méthode ne tente pas d’afficher des informations sur un objet `null` ou sur une forme dont l’aire est nulle. 

[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]
  
Notez que la clause `when` dans l’exemple qui tente de tester si un objet `Shape` est `null` ne s’exécute pas. Le modèle de type correct à utiliser pour tester un `null` est `case null:`.

## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../../includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  

 [Informations de référence sur C#](../index.md)   
 [Guide de programmation C#](../../programming-guide/index.md)   
 [Mots clés C#](index.md)   
 [if-else](if-else.md)   
 [Critères spéciaux](../../pattern-matching.md)   
 

 
