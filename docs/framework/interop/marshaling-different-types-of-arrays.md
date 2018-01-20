---
title: "Marshaling de différents types de tableaux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- marshaling, Arrays sample
- data marshaling, Arrays sample
ms.assetid: c5ac9920-5b6e-4dc9-bf2d-1f6f8ad3b0bf
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1102243eaf43eeb87b16bb654568ef15a821214c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-different-types-of-arrays"></a><span data-ttu-id="ee0a0-102">Marshaling de différents types de tableaux</span><span class="sxs-lookup"><span data-stu-id="ee0a0-102">Marshaling Different Types of Arrays</span></span>
<span data-ttu-id="ee0a0-103">Un tableau est un type référence compris dans du code managé qui contient un ou plusieurs éléments du même type.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-103">An array is a reference type in managed code that contains one or more elements of the same type.</span></span> <span data-ttu-id="ee0a0-104">Même si les tableaux sont des types référence, ils sont passés comme des paramètres In aux fonctions non managées.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-104">Although arrays are reference types, they are passed as In parameters to unmanaged functions.</span></span> <span data-ttu-id="ee0a0-105">Ce comportement est incohérent avec la manière dont les tableaux managés sont passés aux objets managés, c'est-à-dire en tant que paramètres In/Out.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-105">This behavior is inconsistent with way managed arrays are passed to managed objects, which is as In/Out parameters.</span></span> <span data-ttu-id="ee0a0-106">Pour plus d'informations, voir [Copie et épinglage](../../../docs/framework/interop/copying-and-pinning.md).</span><span class="sxs-lookup"><span data-stu-id="ee0a0-106">For additional details, see [Copying and Pinning](../../../docs/framework/interop/copying-and-pinning.md).</span></span>  
  
 <span data-ttu-id="ee0a0-107">Le tableau suivant répertorie les options de marshaling des tableaux et décrit leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-107">The following table lists marshaling options for arrays and describes their usage.</span></span>  
  
|<span data-ttu-id="ee0a0-108">Tableau</span><span class="sxs-lookup"><span data-stu-id="ee0a0-108">Array</span></span>|<span data-ttu-id="ee0a0-109">Description</span><span class="sxs-lookup"><span data-stu-id="ee0a0-109">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ee0a0-110">D'entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-110">Of integers by value.</span></span>|<span data-ttu-id="ee0a0-111">Passe un tableau d'entiers en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-111">Passes an array of integers as an In parameter.</span></span>|  
|<span data-ttu-id="ee0a0-112">D'entiers par référence.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-112">Of integers by reference.</span></span>|<span data-ttu-id="ee0a0-113">Passe un tableau d'entiers en tant que paramètre In/Out.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-113">Passes an array of integers as an In/Out parameter.</span></span>|  
|<span data-ttu-id="ee0a0-114">D'entiers par valeur (à deux dimensions).</span><span class="sxs-lookup"><span data-stu-id="ee0a0-114">Of integers by value (two-dimensional).</span></span>|<span data-ttu-id="ee0a0-115">Passe une matrice d'entiers en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-115">Passes a matrix of integers as an In parameter.</span></span>|  
|<span data-ttu-id="ee0a0-116">De chaînes par valeur.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-116">Of strings by value.</span></span>|<span data-ttu-id="ee0a0-117">Passe un tableau de chaînes en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-117">Passes an array of strings as an In parameter.</span></span>|  
|<span data-ttu-id="ee0a0-118">De structures avec des entiers.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-118">Of structures with integers.</span></span>|<span data-ttu-id="ee0a0-119">Passe un tableau de structures contenant uniquement des entiers en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-119">Passes an array of structures that contain integers as an In parameter.</span></span>|  
|<span data-ttu-id="ee0a0-120">De structures avec des chaînes.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-120">Of structures with strings.</span></span>|<span data-ttu-id="ee0a0-121">Passe un tableau de structures contenant uniquement des entiers en tant que paramètre In/Out.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-121">Passes an array of structures that contain only integers as an In/Out parameter.</span></span> <span data-ttu-id="ee0a0-122">Les membres du tableau peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-122">Members of the array can be changed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee0a0-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="ee0a0-123">Example</span></span>  
 <span data-ttu-id="ee0a0-124">Cet exemple montre comment passer les types de tableaux suivants :</span><span class="sxs-lookup"><span data-stu-id="ee0a0-124">This sample demonstrates how to pass the following types of arrays:</span></span>  
  
-   <span data-ttu-id="ee0a0-125">Tableau d'entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-125">Array of integers by value.</span></span>  
  
-   <span data-ttu-id="ee0a0-126">Tableau d'entiers par référence, qui peut être redimensionné.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-126">Array of integers by reference, which can be resized.</span></span>  
  
-   <span data-ttu-id="ee0a0-127">Tableau multidimensionnel (matrice) d'entiers par valeur.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-127">Multidimensional array (matrix) of integers by value.</span></span>  
  
-   <span data-ttu-id="ee0a0-128">Tableau de chaînes par valeur.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-128">Array of strings by value.</span></span>  
  
-   <span data-ttu-id="ee0a0-129">Tableau de structures avec des entiers.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-129">Array of structures with integers.</span></span>  
  
-   <span data-ttu-id="ee0a0-130">Tableau de structures avec des chaînes.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-130">Array of structures with strings.</span></span>  
  
 <span data-ttu-id="ee0a0-131">À moins qu'un tableau ne soit explicitement marshalé par référence, le comportement par défaut marshale le tableau en tant que paramètre In.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-131">Unless an array is explicitly marshaled by reference, the default behavior marshals the array as an In parameter.</span></span> <span data-ttu-id="ee0a0-132">Vous pouvez modifier ce comportement en appliquant explicitement les attributs <xref:System.Runtime.InteropServices.InAttribute> et <xref:System.Runtime.InteropServices.OutAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ee0a0-132">You can change this behavior by applying the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes explicitly.</span></span>  
  
 <span data-ttu-id="ee0a0-133">L'exemple Tableaux utilise les fonctions non managées ci-dessous, accompagnées de leur déclaration de fonction d'origine :</span><span class="sxs-lookup"><span data-stu-id="ee0a0-133">The Arrays sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="ee0a0-134">**TestArrayOfInts** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-134">**TestArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfInts(int* pArray, int pSize);  
    ```  
  
-   <span data-ttu-id="ee0a0-135">**TestRefArrayOfInts** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-135">**TestRefArrayOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestRefArrayOfInts(int** ppArray, int* pSize);  
    ```  
  
-   <span data-ttu-id="ee0a0-136">**TestMatrixOfInts** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-136">**TestMatrixOfInts** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestMatrixOfInts(int pMatrix[][COL_DIM], int row);  
    ```  
  
-   <span data-ttu-id="ee0a0-137">**TestArrayOfStrings** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-137">**TestArrayOfStrings** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStrings(char** ppStrArray, int size);  
    ```  
  
-   <span data-ttu-id="ee0a0-138">**TestArrayOfStructs** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-138">**TestArrayOfStructs** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs(MYPOINT* pPointArray, int size);  
    ```  
  
-   <span data-ttu-id="ee0a0-139">**TestArrayOfStructs2** exporté depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-139">**TestArrayOfStructs2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    int TestArrayOfStructs2 (MYPERSON* pPersonArray, int size);  
    ```  
  
 <span data-ttu-id="ee0a0-140">[PinvokeLib.dll](http://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614) est une bibliothèque non managée personnalisée qui contient des implémentations pour les fonctions précédemment répertoriées et les deux variables de structure **MYPOINT** et **MYPERSON**.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-140">[PinvokeLib.dll](http://msdn.microsoft.com/library/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains implementations for the previously listed functions and two structure variables, **MYPOINT** and **MYPERSON**.</span></span> <span data-ttu-id="ee0a0-141">Ces structures contiennent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ee0a0-141">The structures contain the following elements:</span></span>  
  
```  
typedef struct _MYPOINT  
{  
   int x;   
   int y;   
} MYPOINT;  
  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON;  
```  
  
 <span data-ttu-id="ee0a0-142">Dans cet exemple, les structures `MyPoint` et `MyPerson` contiennent des types incorporés.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-142">In this sample, the `MyPoint` and `MyPerson` structures contain embedded types.</span></span> <span data-ttu-id="ee0a0-143">L'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> est défini pour s'assurer que les membres soient disposés en mémoire de manière séquentielle, dans l'ordre dans lequel ils apparaissent.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-143">The <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute is set to ensure that the members are arranged in memory sequentially, in the order in which they appear.</span></span>  
  
 <span data-ttu-id="ee0a0-144">La classe `LibWrap` contient un ensemble de méthodes appelé par la classe `App`.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-144">The `LibWrap` class contains a set of methods called by the `App` class.</span></span> <span data-ttu-id="ee0a0-145">Pour obtenir des détails spécifiques sur le passage de tableaux, voir les commentaires de l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-145">For specific details about passing arrays, see the comments in the following sample.</span></span> <span data-ttu-id="ee0a0-146">Un tableau, qui est un type référence, est passé en tant que paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-146">An array, which is a reference type, is passed as an In parameter by default.</span></span> <span data-ttu-id="ee0a0-147">Pour que l'appelant reçoive les résultats, **InAttribute** et **OutAttribute** doivent être appliqués explicitement à l'argument contenant le tableau.</span><span class="sxs-lookup"><span data-stu-id="ee0a0-147">For the caller to receive the results, **InAttribute** and **OutAttribute** must be applied explicitly to the argument containing the array.</span></span>  
  
### <a name="declaring-prototypes"></a><span data-ttu-id="ee0a0-148">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="ee0a0-148">Declaring Prototypes</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#31)]
 [!code-vb[Conceptual.Interop.Marshaling#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#31)]  
  
### <a name="calling-functions"></a><span data-ttu-id="ee0a0-149">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="ee0a0-149">Calling Functions</span></span>  
 [!code-csharp[Conceptual.Interop.Marshaling#32](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/arrays.cs#32)]
 [!code-vb[Conceptual.Interop.Marshaling#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/arrays.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="ee0a0-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee0a0-150">See Also</span></span>  
 [<span data-ttu-id="ee0a0-151">Marshaling des tableaux de types</span><span class="sxs-lookup"><span data-stu-id="ee0a0-151">Marshaling Arrays of Types</span></span>](http://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [<span data-ttu-id="ee0a0-152">Types de données d’appel de plateforme</span><span class="sxs-lookup"><span data-stu-id="ee0a0-152">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="ee0a0-153">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="ee0a0-153">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
