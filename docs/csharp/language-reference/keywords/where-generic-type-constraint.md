---
title: "where (contrainte de type générique) (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: e5baa75c55d58a4d975fc42472f90ff4125cbb5c
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="where-generic-type-constraint-c-reference"></a>where (contrainte de type générique) (Référence C#)
Dans une définition de type générique, la clause `where` permet de spécifier des contraintes sur les types qui peuvent être utilisés comme arguments pour un paramètre de type défini dans une déclaration générique. Vous pouvez, par exemple, déclarer une classe générique, `MyGenericClass`, telle que le paramètre de type `T` implémente l’interface <xref:System.IComparable%601> :  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  Pour plus d’informations sur la clause where dans une expression de requête, consultez [where, clause](../../../csharp/language-reference/keywords/where-clause.md).  
  
 Outre les contraintes d’interface, une clause `where` peut contenir une contrainte de classe de base qui déclare qu’un type doit avoir la classe spécifiée en tant que classe de base (ou être cette classe) pour être utilisé comme un argument de type pour ce type générique. Si une telle contrainte est utilisée, elle doit apparaître avant toute autre contrainte pesant sur ce paramètre de type.  
  
 [!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 La clause `where` peut également inclure une contrainte de constructeur. Il est possible de créer une instance d’un paramètre de type à l’aide de l’opérateur new ; toutefois, il est nécessaire que le paramètre de type soit contraint par la contrainte du constructeur, `new()`. La [contrainte new()](../../../csharp/language-reference/keywords/new-constraint.md) fait savoir au compilateur que tout argument de type fourni doit avoir un constructeur accessible sans paramètre, ou par défaut. Exemple :  
  
 [!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 La contrainte `new()` apparaît en dernier dans la clause `where`.  
  
 Avec plusieurs paramètres de type, utilisez une clause `where` pour chaque paramètre de type, par exemple :  
  
 [!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 Vous pouvez également joindre des contraintes aux paramètres de type des méthodes génériques, comme ceci :  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 Notez que la syntaxe décrivant les contraintes de paramètre de type sur les délégués est la même que celle des méthodes :  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 Pour plus d’informations sur les délégués génériques, consultez [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
 Pour plus d’informations sur la syntaxe et l’utilisation de contraintes, consultez [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [new, contrainte](../../../csharp/language-reference/keywords/new-constraint.md)   
 [Contraintes sur les paramètres de type](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
