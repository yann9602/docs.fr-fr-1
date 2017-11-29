---
title: "Comment : effectuer sans risque un cast du type bool? en bool (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a>Comment : effectuer sans risque un cast du type bool? en bool (Guide de programmation C#)
Le type Nullable `bool?` peut contenir trois valeurs différentes : `true`, `false` et `null`. Par conséquent, le type `bool?` ne peut pas être utilisé dans des instructions conditionnelles comme `if`, `for` ou `while`. Par exemple, le code suivant génère une erreur du compilateur.  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 Cela n’est pas autorisé, car il est difficile de savoir ce que `null` signifie dans le contexte d’une instruction conditionnelle. Pour utiliser un `bool?` dans une instruction conditionnelle, examinez d’abord sa propriété <xref:System.Nullable%601.HasValue%2A> pour vérifier que sa valeur n’est pas `null`, puis castez-le en `bool`. Pour plus d'informations, consultez [bool](../../../csharp/language-reference/keywords/bool.md). Si vous effectuez le cast sur un `bool?` avec la valeur `null`, une exception <xref:System.InvalidOperationException> est levée dans le test conditionnel. L’exemple suivant illustre une façon d’effectuer sans risque un cast de `bool?` en `bool` :  
  
## <a name="example"></a>Exemple  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés littéraux](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)  
 [?? Opérateur](../../../csharp/language-reference/operators/null-conditional-operator.md)
