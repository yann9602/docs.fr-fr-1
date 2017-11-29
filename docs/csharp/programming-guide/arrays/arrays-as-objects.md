---
title: Tableaux en tant qu'objets (guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="9c1d0-102">Tableaux en tant qu'objets (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9c1d0-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="9c1d0-103">En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++.</span><span class="sxs-lookup"><span data-stu-id="9c1d0-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="9c1d0-104"><xref:System.Array> est le type de base abstrait de tous les types de tableau.</span><span class="sxs-lookup"><span data-stu-id="9c1d0-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="9c1d0-105">Vous pouvez utiliser les propriétés et les autres membres de classe de ce type <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="9c1d0-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="9c1d0-106">Vous pourriez, par exemple, utiliser la propriété <xref:System.Array.Length%2A> pour obtenir la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="9c1d0-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="9c1d0-107">Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="9c1d0-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="9c1d0-108">La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.</span><span class="sxs-lookup"><span data-stu-id="9c1d0-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c1d0-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c1d0-109">Example</span></span>  
 <span data-ttu-id="9c1d0-110">L’exemple suivant utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="9c1d0-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9c1d0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c1d0-111">See Also</span></span>  
 [<span data-ttu-id="9c1d0-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9c1d0-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9c1d0-113">Tableaux</span><span class="sxs-lookup"><span data-stu-id="9c1d0-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="9c1d0-114">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="9c1d0-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="9c1d0-115">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="9c1d0-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="9c1d0-116">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="9c1d0-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
