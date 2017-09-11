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
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="f2b58-102">Comment : effectuer sans risque un cast du type bool? en bool (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="f2b58-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="f2b58-103">Le type Nullable `bool?` peut contenir trois valeurs différentes : `true`, `false` et `null`.</span><span class="sxs-lookup"><span data-stu-id="f2b58-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="f2b58-104">Par conséquent, le type `bool?` ne peut pas être utilisé dans des instructions conditionnelles comme `if`, `for` ou `while`.</span><span class="sxs-lookup"><span data-stu-id="f2b58-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="f2b58-105">Par exemple, le code suivant génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="f2b58-105">For example, the following code causes a compiler error.</span></span>  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="f2b58-106">Cela n’est pas autorisé, car il est difficile de savoir ce que `null` signifie dans le contexte d’une instruction conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="f2b58-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="f2b58-107">Pour utiliser un `bool?` dans une instruction conditionnelle, examinez d’abord sa propriété <xref:System.Nullable%601.HasValue%2A> pour vérifier que sa valeur n’est pas `null`, puis castez-le en `bool`.</span><span class="sxs-lookup"><span data-stu-id="f2b58-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="f2b58-108">Pour plus d'informations, consultez [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="f2b58-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="f2b58-109">Si vous effectuez le cast sur un `bool?` avec la valeur `null`, une exception <xref:System.InvalidOperationException> est levée dans le test conditionnel.</span><span class="sxs-lookup"><span data-stu-id="f2b58-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="f2b58-110">L’exemple suivant illustre une façon d’effectuer sans risque un cast de `bool?` en `bool` :</span><span class="sxs-lookup"><span data-stu-id="f2b58-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2b58-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="f2b58-111">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2b58-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2b58-112">See Also</span></span>  
 <span data-ttu-id="f2b58-113">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2b58-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f2b58-114">[Mots clés littéraux](../../../csharp/language-reference/keywords/literal-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="f2b58-114">[Literal Keywords](../../../csharp/language-reference/keywords/literal-keywords.md) </span></span>  
 <span data-ttu-id="f2b58-115">[Types Nullable](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="f2b58-115">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="f2b58-116">?? Opérateur</span><span class="sxs-lookup"><span data-stu-id="f2b58-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)

