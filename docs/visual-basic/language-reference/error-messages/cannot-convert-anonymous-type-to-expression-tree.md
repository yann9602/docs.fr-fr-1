---
title: "Impossible de convertir le type anonyme en arborescence de l’expression, car elle contient un champ qui sert à initialiser un autre champ"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36548
- vbc36548
helpviewer_keywords: BC36548
ms.assetid: 27de068f-080e-4160-86bf-1ec23fd1925a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c2cf8a40060359393807cfb648c46fef9ed853af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-convert-anonymous-type-to-expression-tree-because-it-contains-a-field-that-is-used-in-the-initialization-of-another-field"></a><span data-ttu-id="02e2b-102">Impossible de convertir le type anonyme en arborescence de l’expression, car elle contient un champ qui sert à initialiser un autre champ</span><span class="sxs-lookup"><span data-stu-id="02e2b-102">Cannot convert anonymous type to expression tree because it contains a field that is used in the initialization of another field</span></span>
<span data-ttu-id="02e2b-103">Le compilateur n’accepte pas de conversion d’anonyme en arborescence d’expression lorsqu’une propriété du type anonyme est utilisée pour initialiser une autre propriété du type anonyme.</span><span class="sxs-lookup"><span data-stu-id="02e2b-103">The compiler does not accept conversion of an anonymous to an expression tree when one property of the anonymous type is used to initialize another property of the anonymous type.</span></span> <span data-ttu-id="02e2b-104">Par exemple, dans le code suivant, `Prop1` déclaré dans la liste d’initialisation et puis utilisé comme valeur initiale pour `Prop2`.</span><span class="sxs-lookup"><span data-stu-id="02e2b-104">For example, in the following code, `Prop1` is declared in the initialization list and then used as the initial value for `Prop2`.</span></span>  
  
```vb  
Module M2  
  
    Sub ExpressionExample(Of T)(ByVal x As Expressions.Expression(Of Func(Of T)))  
    End Sub  
  
    Sub Main()  
        ' The following line causes the error.  
        ' ExpressionExample(Function() New With {.Prop1 = 2, .Prop2 = .Prop1})  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="02e2b-105">**ID d’erreur :** BC36548</span><span class="sxs-lookup"><span data-stu-id="02e2b-105">**Error ID:** BC36548</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02e2b-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="02e2b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="02e2b-107">Assignez la valeur initiale pour `Prop1` à une variable locale.</span><span class="sxs-lookup"><span data-stu-id="02e2b-107">Assign the initial value for `Prop1` to a local variable.</span></span> <span data-ttu-id="02e2b-108">Assignez cette variable à la fois aux `Prop1` et `Prop2`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="02e2b-108">Assign that variable to both `Prop1` and `Prop2`, as shown in the following code.</span></span>  
  
    ```  
    Sub Main()  
  
        Dim temp = 2  
        ExpressionExample(Function() New With {.Prop1 = temp, .Prop2 = temp})  
  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="02e2b-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02e2b-109">See Also</span></span>  
 [<span data-ttu-id="02e2b-110">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="02e2b-110">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="02e2b-111">Arborescences de l’expression</span><span class="sxs-lookup"><span data-stu-id="02e2b-111">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)  
 [<span data-ttu-id="02e2b-112">Guide pratique : utiliser des arborescences d’expression pour générer des requêtes dynamiques</span><span class="sxs-lookup"><span data-stu-id="02e2b-112">How to: Use Expression Trees to Build Dynamic Queries</span></span>](http://msdn.microsoft.com/library/1e37e0cc-eef3-48bb-8b69-3adabf322735)
