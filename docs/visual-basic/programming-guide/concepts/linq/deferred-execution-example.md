---
title: "Différé de l’exemple d’exécution (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 9a22bea1-c755-4aac-800a-fcd9e5107ace
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 04839f4f729158406c3107f2dcdfbff74753c29c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="deferred-execution-example-visual-basic"></a><span data-ttu-id="5a2d4-102">Exemple d’exécution différée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a2d4-102">Deferred Execution Example (Visual Basic)</span></span>
<span data-ttu-id="5a2d4-103">Cette rubrique montre comment l'exécution et l'évaluation différées affectent l'exécution de vos requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="5a2d4-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a2d4-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="5a2d4-104">Example</span></span>  
 <span data-ttu-id="5a2d4-105">L'exemple suivant illustre l'ordre d'exécution lors de l'utilisation d'une méthode d'extension qui utilise l'exécution différée.</span><span class="sxs-lookup"><span data-stu-id="5a2d4-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="5a2d4-106">L'exemple déclare un tableau de trois chaînes.</span><span class="sxs-lookup"><span data-stu-id="5a2d4-106">The example declares an array of three strings.</span></span> <span data-ttu-id="5a2d4-107">Il itère ensuite au sein de la collection retournée par `ConvertCollectionToUpperCase`.</span><span class="sxs-lookup"><span data-stu-id="5a2d4-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module Module1  
  
    <Extension()>  
    Private Iterator Function ConvertCollectionToUpperCase(  
    ByVal source As IEnumerable(Of String)) _  
    As IEnumerable(Of String)   
        For Each str As String In source  
            Console.WriteLine("ToUpper: source {0}", str)   
            Yield str.ToUpper()  
        Next  
    End Function  
  
    Sub Main()  
        Dim stringArray = New String() {"abc", "def", "ghi"}  
  
        Dim q = From str In stringArray.ConvertCollectionToUpperCase()  
                Select str  
  
        For Each Str As String In q  
            Console.WriteLine("Main: str {0}", Str)   
        Next  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="5a2d4-108">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5a2d4-108">This example produces the following output:</span></span>  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="5a2d4-109">Notez que lors de l'itération de la collection retournée par `ConvertCollectionToUpperCase`, chaque élément est récupéré du tableau de chaînes source et converti en majuscules avant que l'élément suivant ne soit récupéré du tableau de chaînes source.</span><span class="sxs-lookup"><span data-stu-id="5a2d4-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="5a2d4-110">Vous pouvez constater que l'intégralité du tableau de chaînes n'est pas convertie en majuscules avant que chaque élément de la collection retournée n'ait été traité dans la boucle `foreach` dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="5a2d4-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2d4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a2d4-111">See Also</span></span>  
 [<span data-ttu-id="5a2d4-112">Didacticiel : Différée de l’exécution (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a2d4-112">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
