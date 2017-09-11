---
title: Tableaux en tant qu'objets (guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
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
ms.openlocfilehash: 396d0df9196b7331e94127730b83782ffc8ea593
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="ad3e8-102">Tableaux en tant qu'objets (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ad3e8-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="ad3e8-103">En C#, les tableaux sont en fait des objets, et pas simplement des zones adressables de mémoire contiguë comme en C et C++.</span><span class="sxs-lookup"><span data-stu-id="ad3e8-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="ad3e8-104"><xref:System.Array> est le type de base abstrait de tous les types de tableau.</span><span class="sxs-lookup"><span data-stu-id="ad3e8-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="ad3e8-105">Vous pouvez utiliser les propriétés et les autres membres de classe de ce type <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="ad3e8-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="ad3e8-106">Vous pourriez, par exemple, utiliser la propriété <xref:System.Array.Length%2A> pour obtenir la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="ad3e8-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="ad3e8-107">Le code suivant affecte la longueur du tableau `numbers`, c’est-à-dire la valeur `5`, à une variable appelée `lengthOfNumbers` :</span><span class="sxs-lookup"><span data-stu-id="ad3e8-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 <span data-ttu-id="ad3e8-108">[!code-cs[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad3e8-108">[!code-cs[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]</span></span>  
  
 <span data-ttu-id="ad3e8-109">La classe <xref:System.Array> fournit beaucoup d’autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.</span><span class="sxs-lookup"><span data-stu-id="ad3e8-109">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad3e8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="ad3e8-110">Example</span></span>  
 <span data-ttu-id="ad3e8-111">L’exemple suivant utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="ad3e8-111">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 <span data-ttu-id="ad3e8-112">[!code-cs[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ad3e8-112">[!code-cs[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3e8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad3e8-113">See Also</span></span>  
 <span data-ttu-id="ad3e8-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad3e8-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ad3e8-115">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="ad3e8-115">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="ad3e8-116">[Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="ad3e8-116">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="ad3e8-117">[Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="ad3e8-117">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="ad3e8-118">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="ad3e8-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

