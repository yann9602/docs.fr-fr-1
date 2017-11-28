---
title: Tableaux multidimensionnels (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab3a93c21ddb9541a6149967605b851ea5a50a3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="d96dd-102">Tableaux multidimensionnels (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d96dd-102">Multidimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="d96dd-103">Les tableaux peuvent avoir plusieurs dimensions.</span><span class="sxs-lookup"><span data-stu-id="d96dd-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="d96dd-104">Par exemple, la déclaration suivante crée un tableau à deux dimensions composé de quatre lignes et deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="d96dd-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 <span data-ttu-id="d96dd-105">La déclaration suivante crée un tableau de trois dimensions, 4, 2 et 3.</span><span class="sxs-lookup"><span data-stu-id="d96dd-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="d96dd-106">Initialisation du tableau</span><span class="sxs-lookup"><span data-stu-id="d96dd-106">Array Initialization</span></span>  
 <span data-ttu-id="d96dd-107">Vous pouvez initialiser le tableau au moment de la déclaration, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d96dd-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 <span data-ttu-id="d96dd-108">Vous pouvez aussi initialiser le tableau sans spécifier de rang.</span><span class="sxs-lookup"><span data-stu-id="d96dd-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 <span data-ttu-id="d96dd-109">Si vous choisissez de déclarer une variable de tableau sans initialisation, vous devez utiliser l’opérateur `new` pour assigner un tableau à la variable.</span><span class="sxs-lookup"><span data-stu-id="d96dd-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="d96dd-110">L’utilisation de `new` est illustrée dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d96dd-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 <span data-ttu-id="d96dd-111">L’exemple suivant assigne une valeur à un élément de tableau particulier.</span><span class="sxs-lookup"><span data-stu-id="d96dd-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 <span data-ttu-id="d96dd-112">De la même manière, l’exemple suivant obtient la valeur d’un élément de tableau particulier et l’affecte à la variable `elementValue`.</span><span class="sxs-lookup"><span data-stu-id="d96dd-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 <span data-ttu-id="d96dd-113">L’exemple de code suivant initialise les éléments de tableau avec les valeurs par défaut (sauf pour les tableaux en escalier).</span><span class="sxs-lookup"><span data-stu-id="d96dd-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d96dd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d96dd-114">See Also</span></span>  
 [<span data-ttu-id="d96dd-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d96dd-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d96dd-116">Tableaux</span><span class="sxs-lookup"><span data-stu-id="d96dd-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="d96dd-117">Tableaux unidimensionnels</span><span class="sxs-lookup"><span data-stu-id="d96dd-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="d96dd-118">Tableaux en escalier</span><span class="sxs-lookup"><span data-stu-id="d96dd-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
