---
title: "Comment : effectuer sans risque un cast du type bool? en bool (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: 9
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
ms.openlocfilehash: c8a3dc3280b7dca802b327d9454c7f0ba9ed44be
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

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

