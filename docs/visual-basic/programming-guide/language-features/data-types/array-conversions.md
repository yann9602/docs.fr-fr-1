---
title: Conversion des tableaux (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 40dc9805157dd0bc991ca2375c3436aa6b6e09a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="array-conversions-visual-basic"></a><span data-ttu-id="ddd53-102">Conversion des tableaux (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ddd53-102">Array Conversions (Visual Basic)</span></span>
<span data-ttu-id="ddd53-103">Vous pouvez convertir un type tableau vers un autre type fourni les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="ddd53-103">You can convert an array type to a different array type provided you meet the following conditions:</span></span>  
  
-   <span data-ttu-id="ddd53-104">**Rang égal.**</span><span class="sxs-lookup"><span data-stu-id="ddd53-104">**Equal Rank.**</span></span> <span data-ttu-id="ddd53-105">Les rangs des deux tableaux doivent être identiques, autrement dit, ils doivent avoir le même nombre de dimensions.</span><span class="sxs-lookup"><span data-stu-id="ddd53-105">The ranks of the two arrays must be the same, that is, they must have the same number of dimensions.</span></span> <span data-ttu-id="ddd53-106">Toutefois, les longueurs des dimensions respectives n’avez pas besoin être les mêmes.</span><span class="sxs-lookup"><span data-stu-id="ddd53-106">However, the lengths of the respective dimensions do not need to be the same.</span></span>  
  
-   <span data-ttu-id="ddd53-107">**Type de données d’élément.**</span><span class="sxs-lookup"><span data-stu-id="ddd53-107">**Element Data Type.**</span></span> <span data-ttu-id="ddd53-108">Les types de données des éléments des deux tableaux doivent être des types référence.</span><span class="sxs-lookup"><span data-stu-id="ddd53-108">The data types of the elements of both arrays must be reference types.</span></span> <span data-ttu-id="ddd53-109">Vous ne pouvez pas convertir un `Integer` de tableau à un `Long` ou même à un `Object` de tableau, car au moins un type valeur est impliqué.</span><span class="sxs-lookup"><span data-stu-id="ddd53-109">You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved.</span></span> <span data-ttu-id="ddd53-110">Pour plus d’informations, consultez [les Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="ddd53-110">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
-   <span data-ttu-id="ddd53-111">**Convertibilité.**</span><span class="sxs-lookup"><span data-stu-id="ddd53-111">**Convertibility.**</span></span> <span data-ttu-id="ddd53-112">Une conversion restrictive ou étendue doit être possible entre les types d’éléments des deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="ddd53-112">A conversion, either widening or narrowing, must be possible between the element types of the two arrays.</span></span> <span data-ttu-id="ddd53-113">Un exemple qui ne satisfait pas cette condition est une tentative de conversion entre un `String` tableau et un tableau d’une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ddd53-113">An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ddd53-114">Ces deux types n’ont rien en commun et aucune conversion n’existe entre eux.</span><span class="sxs-lookup"><span data-stu-id="ddd53-114">These two types have nothing in common, and no conversion of any kind exists between them.</span></span>  
  
 <span data-ttu-id="ddd53-115">Une conversion de type d’un tableau à un autre élargissent ou selon si la conversion des éléments respectifs est restrictive ou étendue.</span><span class="sxs-lookup"><span data-stu-id="ddd53-115">A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing.</span></span> <span data-ttu-id="ddd53-116">Pour plus d’informations, consultez [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="ddd53-116">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="conversion-to-an-object-array"></a><span data-ttu-id="ddd53-117">Conversion en un tableau d’objets</span><span class="sxs-lookup"><span data-stu-id="ddd53-117">Conversion to an Object Array</span></span>  
 <span data-ttu-id="ddd53-118">Lorsque vous déclarez un `Object` tableau sans l’initialiser, son type d’élément est `Object` tant qu’il reste sans être initialisé.</span><span class="sxs-lookup"><span data-stu-id="ddd53-118">When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized.</span></span> <span data-ttu-id="ddd53-119">Lorsque vous la définissez dans un tableau d’une classe spécifique, il prend le type de cette classe.</span><span class="sxs-lookup"><span data-stu-id="ddd53-119">When you set it to an array of a specific class, it takes on the type of that class.</span></span> <span data-ttu-id="ddd53-120">Toutefois, son type sous-jacent est toujours `Object`, et vous pouvez ensuite le configurer en un autre tableau de classe non apparentée.</span><span class="sxs-lookup"><span data-stu-id="ddd53-120">However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class.</span></span> <span data-ttu-id="ddd53-121">Étant donné que toutes les classes dérivent à partir de `Object`, vous pouvez modifier le type d’élément du tableau à partir de n’importe quelle classe à une autre classe.</span><span class="sxs-lookup"><span data-stu-id="ddd53-121">Since all classes derive from `Object`, you can change the array's element type from any class to any other class.</span></span>  
  
 <span data-ttu-id="ddd53-122">Dans l’exemple suivant, aucune conversion n’existe entre les types `student` et `String`, mais les deux dérivent `Object`, de sorte que toutes les affectations sont valides.</span><span class="sxs-lookup"><span data-stu-id="ddd53-122">In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.</span></span>  
  
```  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a><span data-ttu-id="ddd53-123">Type sous-jacent d’un tableau</span><span class="sxs-lookup"><span data-stu-id="ddd53-123">Underlying Type of an Array</span></span>  
 <span data-ttu-id="ddd53-124">Si vous déclarez à l’origine d’un tableau avec une classe particulière, son type d’élément sous-jacent est cette classe.</span><span class="sxs-lookup"><span data-stu-id="ddd53-124">If you originally declare an array with a specific class, its underlying element type is that class.</span></span> <span data-ttu-id="ddd53-125">Si vous lui affectez par la suite à un tableau d’une autre classe, il doit y avoir une conversion entre les deux classes.</span><span class="sxs-lookup"><span data-stu-id="ddd53-125">If you subsequently set it to an array of another class, there must be a conversion between the two classes.</span></span>  
  
 <span data-ttu-id="ddd53-126">Dans l’exemple suivant, `students` est un `student` tableau.</span><span class="sxs-lookup"><span data-stu-id="ddd53-126">In the following example, `students` is a `student` array.</span></span> <span data-ttu-id="ddd53-127">Dans la mesure où il n’existe aucune conversion entre `String` et `student`, la dernière instruction échoue.</span><span class="sxs-lookup"><span data-stu-id="ddd53-127">Since no conversion exists between `String` and `student`, the last statement fails.</span></span>  
  
```  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddd53-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddd53-128">See Also</span></span>  
 [<span data-ttu-id="ddd53-129">Types de données</span><span class="sxs-lookup"><span data-stu-id="ddd53-129">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="ddd53-130">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ddd53-130">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="ddd53-131">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="ddd53-131">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="ddd53-132">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="ddd53-132">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="ddd53-133">Comment : convertir un objet en un autre Type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ddd53-133">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="ddd53-134">Types de données</span><span class="sxs-lookup"><span data-stu-id="ddd53-134">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="ddd53-135">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="ddd53-135">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ddd53-136">Tableaux</span><span class="sxs-lookup"><span data-stu-id="ddd53-136">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
