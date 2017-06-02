---
title: Membres expression-bodied (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: b77f656d36dc4f0a715755e13bfcd6c3515c697b
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="expression-bodied-members-c-programming-guide"></a>Membres expression-bodied (Guide de programmation C#)
Les définitions de corps d’expression vous permettent de fournir l’implémentation d’un membre sous une forme lisible et très concise. Vous pouvez utiliser une définition de corps d’expression chaque fois que la logique d’un membre pris en charge, comme une méthode ou une propriété, se compose d’une seule expression. La syntaxe générale d’une définition de corps d’expression est la suivante :

```csharp
member => expression;
```

où *expression* est une expression valide. 

La prise en charge des définitions de corps d’expression a été introduite pour les méthodes et les accesseurs get de propriétés dans C# 6, et a été étendue dans C# 7. Vous pouvez utiliser des définitions de corps d’expression avec les membres de type listés dans le tableau suivant : 

|Membre  |Prise en charge à compter de |
|---------|---------|
|[Méthode](#methods)  |C# 6 |
|[Constructeur](#constructors)   |C# 7 |
|[Finaliseur](#finalizers)     |C# 7 |
|[Accesseur get de propriété](#property-get-statements)  |C# 6 |
|[Accesseur set de propriété](#property-set-statements)  |C# 7 |
|[Indexeur](#indexers)       |C# 7 |

## <a name="methods"></a>Méthodes

Une méthode expression-bodied se compose d’une seule expression qui retourne une valeur dont le type correspond au type de retour de la méthode ou, pour les méthodes qui retournent `void`, qui effectue une opération. Par exemple, les types qui substituent la méthode <xref:System.Object.ToString%2A> incluent généralement une expression unique qui retourne la représentation sous forme de chaîne de l’objet actuel. 

L’exemple suivant définit une classe `Person` qui substitue la méthode <xref:System.Object.ToString%2A> avec une définition de corps d’expression. Il définit également une méthode `Show` qui affiche un nom sur la console. Notez que le mot clé `return` n’est pas utilisé dans la définition de corps d’expression `ToString`.

[!code-cs[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

Pour plus d’informations, consultez [Méthodes (Guide de programmation C#)](../classes-and-structs/methods.md).
 
## <a name="constructors"></a>Constructeurs

Une définition de corps d’expression pour un constructeur se compose généralement d’une seule expression d’assignation ou d’un appel de méthode qui gère les arguments du constructeur ou qui initialise l’état de l’instance. 

L’exemple suivant définit une classe `Location` dont le constructeur a un seul paramètre de chaîne nommé *name*. La définition de corps d’expression assigne l’argument à la propriété `Name`.

[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Pour plus d’informations, consultez [Constructeurs (Guide de programmation C#)](../classes-and-structs/constructors.md).

## <a name="finalizers"></a>Finaliseurs

Une définition de corps d’expression pour un finaliseur contient généralement des instructions de nettoyage, telles que des instructions qui libèrent les ressources non managées.

L’exemple suivant définit un finaliseur qui utilise une définition de corps d’expression pour indiquer que le finaliseur a été appelé.

[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

Pour plus d’informations, consultez [Finaliseurs (Guide de programmation C#)](../classes-and-structs/destructors.md).

## <a name="property-get-statements"></a>Instructions get de propriété

Si vous choisissez d’implémenter un accesseur get de propriété vous-même, vous pouvez utiliser une définition de corps d’expression pour les expressions uniques qui retournent simplement la valeur de propriété. Notez que l’instruction `return` n’est pas utilisée.

L’exemple suivant définit une propriété `Location.Name` dont l’accesseur get de propriété retourne la valeur du champ `locationName` privé qui stocke la propriété. 

[!code-cs[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Les propriétés en lecture seule qui utilisent une définition de corps d’expression peuvent être implémentées sans instruction `set` explicite. La syntaxe est :

```csharp
PropertyName => returnValue;
```

L’exemple suivant définit une classe `Location` dont la propriété `Name` en lecture seule est implémentée en tant que définition de corps d’expression qui retourne la valeur du champ `locationName` privé.

[!code-cs[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

Pour plus d’informations, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).

## <a name="property-set-statements"></a>Instructions set de propriété

Si vous choisissez d’implémenter un accesseur set de propriété vous-même, vous pouvez utiliser une définition de corps d’expression pour une expression à une ligne qui assigne une valeur au champ qui stocke la propriété.

L’exemple suivant définit une propriété `Location.Name` dont l’instruction set de propriété assigne son argument d’entrée au champ `locationName` privé qui stocke la propriété.

[!code-cs[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

Pour plus d’informations, consultez [Propriétés (Guide de programmation C#)](../classes-and-structs/properties.md).

## <a name="indexers"></a>Indexeurs

Comme les propriétés, les accesseurs get et set d’un indexeur sont composés de définitions de corps d’expression si l’accesseur get est constitué d’une seule instruction qui retourne une valeur ou si l’accesseur set effectue une assignation simple.

L’exemple suivant définit une classe nommée `Sports` qui inclut un tableau <xref:System.String> interne contenant les noms de plusieurs sports. Les accesseurs get et set de l’indexeur sont implémentés en tant que définitions de corps d’expression.

[!code-cs[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

Pour plus d’informations, consultez [Indexeurs (Guide de programmation C#)](../indexers/index.md).


