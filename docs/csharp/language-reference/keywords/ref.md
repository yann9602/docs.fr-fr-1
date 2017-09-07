---
title: "ref (référence C#)"
ms.date: 2017-05-30
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ref_CSharpKeyword
- ref
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], ref
- ref keyword [C#]
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
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
ms.openlocfilehash: 003125ca6218d42a919d8bb592b5454a7cb387c7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ref-c-reference"></a>ref (référence C#)

Le mot clé `ref` indique une valeur qui est passée par référence. Il est utilisé dans trois contextes différents : 

- Dans une signature de méthode et dans un appel de méthode, pour passer un argument à une méthode par référence. Pour plus d’informations, consultez [Passage d’un argument par référence](#passing-an-argument-by-reference).

- Dans une signature de méthode, pour retourner une valeur à l’appelant par référence. Pour plus d’informations, consultez [Valeurs de retour de référence](#reference-return-values).

- Dans le corps d’un membre, pour indiquer qu’une valeur de retour de référence est stockée localement sous la forme d’une référence que l’appelant a l’intention de modifier. Pour plus d’informations, consultez [Variables locales ref](#ref-locals).

## <a name="passing-an-argument-by-reference"></a>Passage d’un argument par référence

Quand il est utilisé dans la liste de paramètres d’une méthode, le mot clé `ref` indique qu’un argument est passé par référence, et non par valeur. La conséquence est que toute modification apportée à l’argument dans la méthode appelée est reflétée dans la méthode d’appel. Par exemple, si l’appelant passe une expression de variable locale ou une expression d’accès à un élément de tableau et que la méthode appelée remplace l’objet auquel fait référence le paramètre ref, la variable locale de l’appelant ou l’élément de tableau fait désormais référence au nouvel objet quand la méthode retourne une valeur.

> [!NOTE]
>  Ne confondez pas le concept de passage par référence avec celui de types de référence. Les deux concepts ne sont pas identiques. Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence. Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.  

Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.  

[!code-cs[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-1.cs)]

Un argument passé à un paramètre `ref` doit être initialisé avant d'être transmis. Cette obligation diffère des paramètres [out](out.md), dont les arguments ne doivent pas être explicitement initialisés avant d’être passés.

Les membres d'une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref` et `out`. Une erreur de compilation se produit si la seule différence entre deux membres d'un type est que l'un d'eux a un paramètre `ref`et l'autre un paramètre `out`. Le code suivant, par exemple, ne se compile pas.  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-2.cs)]
  
 Cependant, les méthodes peuvent être surchargées quand une méthode a un paramètre `ref` ou `out`, et que l’autre a un paramètre de valeur, comme illustré dans l’exemple suivant.
  
 [!code-cs[ref-and-overloads](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-3.cs)]
  
 Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `ref` et `out` font partie de la signature et ne correspondent pas l'un à l'autre.  
  
 Les propriétés ne sont pas des variables. Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.  
  
 Pour plus d’informations sur la manière de passer des tableaux, consultez [Passage de tableaux à l’aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :  
  
-   Méthodes async, que vous définissez à l’aide du modificateur [async](../../../csharp/language-reference/keywords/async.md).  
  
-   Les méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  
  
## <a name="passing-an-argument-by-reference-an-example"></a>Passage d’un argument par référence : exemple

Les exemples précédents passent les types valeur par référence. Vous pouvez également utiliser le mot clé `ref` pour passer les types référence par référence. Le passage d’un type référence par référence permet à la méthode appelée de remplacer l’objet auquel fait référence le paramètre de référence dans l’appelant. L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence. Si vous modifiez la valeur de l'emplacement de stockage du paramètre (pour pointer vers un nouvel objet), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant. L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.   
  
 [!code-cs[ReferencesByRef](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-4.cs)]  

Pour plus d’informations sur la manière de passer des types référence par valeur et par référence, consultez [Passage de paramètres de type référence ](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).
  
## <a name="reference-return-values"></a>Valeurs de retour de référence

Les valeurs de retour de référence (ou retours ref) sont des valeurs qu’une méthode retourne par référence à l’appelant. Autrement dit, l’appelant peut modifier la valeur retournée par une méthode, et ce changement est reflété dans l’état de l’objet qui contient la méthode. 

Une valeur de retour de référence est définie à l’aide du mot clé `ref` :

- Dans la signature de la méthode. Par exemple, la signature de méthode suivante indique que la méthode `GetCurrentPrice` retourne une valeur <xref:System.Decimal> par référence.

   ```csharp
   public ref decimal GetCurrentValue()
   ``` 
- Avant chaque instruction `return` dans la méthode. Exemple :
 
   ```csharp
   ref return Decimal.Zero;
   ``` 

Pour que l’appelant modifie l’état d’un objet, la valeur de retour de référence doit être stockée dans une variable qui est explicitement définie comme [variable locale ref](#ref-locals). 

Pour obtenir un exemple, consultez [un exemple de retours ref et de variables locales ref](#a-ref-returns-and-ref-locals-example)

## <a name="ref-locals"></a>Variables locales ref

Une variable locale ref est utilisée pour faire référence aux valeurs retournées à l’aide de `ref return`.  Une variable locale ref doit être initialisée et affectée à une valeur de retour de référence. Toute modification apportée à la valeur de la variable locale ref est reflétée dans l’état de l’objet dont la méthode a retourné la valeur par référence.

Vous définissez une variable locale ref à l’aide du mot clé `ref` avant la déclaration de la variable, ainsi qu’immédiatement avant l’appel à la méthode qui retourne la valeur par référence. 

Par exemple, l’instruction suivante définit une valeur de variable locale ref qui est retournée par une méthode nommée `GetEstimatedValue` :

```csharp
ref decimal estValue = ref Building.GetEstimatedValue();
```

Notez que le mot clé `ref` doit être utilisé aux deux emplacements, sans quoi le compilateur génère l’erreur CS8172, « Impossible d’initialiser une variable par référence avec une valeur ». 
 
## <a name="a-ref-returns-and-ref-locals-example"></a>Exemple de retours ref et de variables locales ref

L’exemple suivant définit une classe `Book` qui a deux champs <xref:System.String>, `Title` et `Author`. Il définit également une classe `BookCollection` qui inclut un tableau privé d’objets `Book`. Des objets livres individuels sont retournés par référence en appelant sa méthode `GetBookByTitle`.

[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#1)]  

Quand l’appelant stocke la valeur retournée par la méthode `GetBookByTitle` comme variable locale ref, les modifications apportées par l’appelant à la valeur de retour sont reflétées dans l’objet `BookCollection`, comme le montre l’exemple suivant.

[!code-cs[csrefreturns](../../../../samples/snippets/csharp/language-reference/keywords/ref/ref-5.cs#2)]  

## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)
