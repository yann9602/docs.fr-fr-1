---
title: Contraintes (F#)
description: "En savoir plus sur F # les contraintes qui s’appliquent aux paramètres de type générique pour spécifier la configuration requise pour un argument de type dans un type générique ou une fonction."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f232a3a-9486-48fb-9759-f23404ed4b52
ms.openlocfilehash: 91854fd2f692688e0f1c27aba1422eff64156048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="constraints"></a>Contraintes

Cette rubrique décrit les contraintes que vous pouvez appliquer aux générique pour spécifier la configuration requise pour un argument de type dans un type générique ou une fonction de paramètres de type.


## <a name="syntax"></a>Syntaxe

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Remarques
Il existe plusieurs contraintes différentes, que vous pouvez appliquer pour limiter les types qui peuvent être utilisés dans un type générique. Le tableau suivant répertorie et décrit ces contraintes.

|Contrainte|Syntaxe|Description|
|----------|------|-----------|
|Contrainte de type|*paramètre de type* :&gt; *type*|Le type fourni doit être égale à ou dérivé du type spécifié ou, si le type est une interface, le type fourni doit implémenter l’interface.|
|Contrainte Null|*paramètre de type* : null|Le type fourni doit prendre en charge le littéral null. Cela inclut tous les types d’objet .NET mais pas F # liste, tuple, fonction, classe, enregistrement ou les types d’union.|
|Contrainte de membre explicite|[()]*paramètre de type* [ou... ou *paramètre de type*)] : (* signature de membre *)|Au moins un des arguments de type fournis doit avoir un membre qui a la signature spécifiée ; non destiné courantes. Les membres doivent être explicitement définies sur le type ou une partie d’une extension de type implicite pour être des cibles valides pour une contrainte de membre explicite.|
|Contrainte de constructeur|*paramètre de type* : (nouveau : unité -&gt; ' un)|Le type fourni doit avoir un constructeur par défaut.|
|Contrainte de Type valeur|: struct|Le type fourni doit être un type valeur .NET.|
|Contrainte de Type référence|: pas de struct|Le type fourni doit être un type référence .NET.|
|Contrainte de Type énumération|: enum&lt;*type sous-jacent*&gt;|Le type fourni doit être un type énuméré qui a le type sous-jacent spécifié ; non destiné courantes.|
|Contrainte de délégué|: déléguer&lt;*type de paramètre de tuple*, *type de retour*&gt;|Le type fourni doit être un type délégué qui a les arguments spécifiés et retourner de valeur ; non destiné courantes.|
|Contrainte de comparaison|: comparaison|Le type fourni doit prendre en charge la comparaison.|
|Contrainte d’égalité|: l’égalité|Le type fourni doit prendre en charge l’égalité.|
|Contrainte non managée|: non managé|Le type fourni doit être un type non managé. Types non managés sont soit certains types primitifs (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, ou `decimal`), types énumération, `nativeptr&lt;_&gt;`, ou une structure non générique dont les champs sont tous les types non managés.|
Vous devez ajouter une contrainte lorsque votre code doit utiliser une fonctionnalité qui est disponible sur le type de contrainte, mais pas sur les types en général. Par exemple, si vous utilisez la contrainte de type pour spécifier un type de classe, vous pouvez utiliser l’une des méthodes de cette classe dans la fonction générique ou d’un type.

Spécification de contraintes est parfois nécessaire lors de l’écriture des paramètres de type explicitement, parce que sans une contrainte, le compilateur n’a aucun moyen de vérifier que les fonctionnalités que vous utilisez sera disponibles sur n’importe quel type qui peut être fourni au moment de l’exécution pour le type paramètre.

Les contraintes plus courantes que vous utilisez dans le code F # sont les contraintes de type qui spécifient des interfaces ou des classes de base. Les autres contraintes sont utilisés par la bibliothèque F # pour implémenter certaines fonctionnalités, telles que la contrainte de membre explicite, qui est utilisée pour implémenter la surcharge d’opérateur pour les opérateurs arithmétiques, ou est fournie principalement parce que F # prend en charge le texte complet ensemble de contraintes qui est pris en charge par le common language runtime.

Pendant le processus d’inférence de type, certaines contraintes sont déduites automatiquement par le compilateur. Par exemple, si vous utilisez la `+` opérateur dans une fonction, le compilateur déduit une contrainte de membre explicite sur les types de variables qui sont utilisés dans l’expression.

Le code suivant illustre quelques déclarations de contrainte.

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>Voir aussi
[Génériques](index.md)

[Contraintes](constraints.md)
