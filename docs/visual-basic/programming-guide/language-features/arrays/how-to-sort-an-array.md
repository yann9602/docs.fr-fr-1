---
title: "Comment : trier un tableau dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 310c2dacb384de49c80073840c6c58d37f3937d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a><span data-ttu-id="413be-102">Comment : trier un tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="413be-102">How to: Sort An Array in Visual Basic</span></span>
<span data-ttu-id="413be-103">Cet exemple déclare un tableau de `String` objets nommés `zooAnimals`, il remplit, puis le tri par ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="413be-103">This example declares an array of `String` objects named `zooAnimals`, populates it, and then sorts it alphabetically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="413be-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="413be-104">Example</span></span>  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="413be-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="413be-105">Compiling the Code</span></span>  
 <span data-ttu-id="413be-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="413be-106">This example requires:</span></span>  
  
-   <span data-ttu-id="413be-107">Accès à Mscorlib.dll et <xref:System> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="413be-107">Access to Mscorlib.dll and the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="413be-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="413be-108">Robust Programming</span></span>  
 <span data-ttu-id="413be-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="413be-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="413be-110">Le tableau est vide (<xref:System.ArgumentNullException> classe)</span><span class="sxs-lookup"><span data-stu-id="413be-110">Array is empty (<xref:System.ArgumentNullException> class)</span></span>  
  
-   <span data-ttu-id="413be-111">Le tableau est multidimensionnel (<xref:System.RankException> classe)</span><span class="sxs-lookup"><span data-stu-id="413be-111">Array is multidimensional (<xref:System.RankException> class)</span></span>  
  
-   <span data-ttu-id="413be-112">Un ou plusieurs éléments du tableau n’implémentent pas le <xref:System.IComparable> interface (<xref:System.InvalidOperationException> classe)</span><span class="sxs-lookup"><span data-stu-id="413be-112">One or more elements of the array do not implement the <xref:System.IComparable> interface (<xref:System.InvalidOperationException> class)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413be-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="413be-113">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="413be-114">Tableaux</span><span class="sxs-lookup"><span data-stu-id="413be-114">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="413be-115">Dépannage des tableaux</span><span class="sxs-lookup"><span data-stu-id="413be-115">Troubleshooting Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [<span data-ttu-id="413be-116">Collections</span><span class="sxs-lookup"><span data-stu-id="413be-116">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [<span data-ttu-id="413be-117">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="413be-117">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
