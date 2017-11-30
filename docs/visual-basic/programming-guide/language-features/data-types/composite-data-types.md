---
title: "Types de données composites (Visual Basic)"
ms.custom: 
ms.date: 04/25/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e9adb407757dbee2f7ac5a94118623a62212faec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="36881-102">Types de données composites (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36881-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="36881-103">Outre les types de données élémentaires [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fournit, vous pouvez assembler des éléments de différents types pour créer *types de données composites* tels que des structures, des tableaux et des classes.</span><span class="sxs-lookup"><span data-stu-id="36881-103">In addition to the elementary data types [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="36881-104">Vous pouvez générer des types de données composites à partir des types élémentaires et d’autres types composites.</span><span class="sxs-lookup"><span data-stu-id="36881-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="36881-105">Par exemple, vous pouvez définir un tableau d’éléments de structure ou une structure avec des membres de tableau.</span><span class="sxs-lookup"><span data-stu-id="36881-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="36881-106">Types de données</span><span class="sxs-lookup"><span data-stu-id="36881-106">Data Types</span></span>  
 <span data-ttu-id="36881-107">Un type composite est différent du type de données d’un de ses composants.</span><span class="sxs-lookup"><span data-stu-id="36881-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="36881-108">Par exemple, un tableau de `Integer` éléments n’est pas le `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="36881-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="36881-109">Un type de données de tableau est généralement représenté à l’aide du type d’élément, parenthèses et des virgules si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="36881-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="36881-110">Par exemple, un tableau unidimensionnel de `String` éléments est représenté en tant que `String()`et un tableau à deux dimensions de `Boolean` éléments est représenté en tant que `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="36881-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="36881-111">Types de structure</span><span class="sxs-lookup"><span data-stu-id="36881-111">Structure Types</span></span>  
 <span data-ttu-id="36881-112">Il n’existe aucun type de données unique comprenant toutes les structures.</span><span class="sxs-lookup"><span data-stu-id="36881-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="36881-113">Au lieu de cela, chaque définition d’une structure représente un type de données unique, même si deux structures définissent des éléments identiques dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="36881-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="36881-114">Toutefois, si vous créez deux ou plusieurs instances de la même structure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] considère qu’ils soient du même type de données.</span><span class="sxs-lookup"><span data-stu-id="36881-114">However, if you create two or more instances of the same structure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="36881-115">Tuples</span><span class="sxs-lookup"><span data-stu-id="36881-115">Tuples</span></span>

<span data-ttu-id="36881-116">Un tuple est une structure léger qui contient deux ou plusieurs champs dont les types sont prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="36881-116">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="36881-117">Tuples sont pris en charge dans Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="36881-117">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="36881-118">Tuples sont couramment utilisés pour retourner plusieurs valeurs à partir d’un seul appel de méthode sans avoir à passer des arguments par référence ou d’empaquetage des champs renvoyés dans une classe ou une structure plus lourdes.</span><span class="sxs-lookup"><span data-stu-id="36881-118">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="36881-119">Consultez le [Tuples](tuples.md) rubrique pour plus d’informations sur les tuples.</span><span class="sxs-lookup"><span data-stu-id="36881-119">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="36881-120">Types de tableau</span><span class="sxs-lookup"><span data-stu-id="36881-120">Array Types</span></span>  
 <span data-ttu-id="36881-121">Il n’existe aucun type de données unique comprenant tous les tableaux.</span><span class="sxs-lookup"><span data-stu-id="36881-121">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="36881-122">Le type de données d’une instance particulière d’un tableau est déterminé par le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="36881-122">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="36881-123">Le fait d’être un tableau</span><span class="sxs-lookup"><span data-stu-id="36881-123">The fact of being an array</span></span>  
  
-   <span data-ttu-id="36881-124">Le rang (nombre de dimensions) du tableau</span><span class="sxs-lookup"><span data-stu-id="36881-124">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="36881-125">Le type d’élément du tableau</span><span class="sxs-lookup"><span data-stu-id="36881-125">The element type of the array</span></span>  
  
 <span data-ttu-id="36881-126">En particulier, la longueur d’une dimension donnée n’est pas partie du type de données de l’instance.</span><span class="sxs-lookup"><span data-stu-id="36881-126">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="36881-127">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="36881-127">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="36881-128">Dans l’exemple précédent, les variables tableau `arrayA` et `arrayB` sont considérés comme étant de même type de données : `Byte()` , même si elles sont initialisées avec des longueurs différentes.</span><span class="sxs-lookup"><span data-stu-id="36881-128">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="36881-129">Variables `arrayB` et `arrayC` ne sont pas du même type car leurs types d’éléments sont différents.</span><span class="sxs-lookup"><span data-stu-id="36881-129">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="36881-130">Variables `arrayC` et `arrayD` ne sont pas du même type, car leurs rangs sont différents.</span><span class="sxs-lookup"><span data-stu-id="36881-130">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="36881-131">Variables `arrayD` et `arrayE` ont le même type — `Short(,)` , car leurs rangs et types d’élément sont identiques, même si `arrayD` n’est pas encore initialisé.</span><span class="sxs-lookup"><span data-stu-id="36881-131">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="36881-132">Pour plus d’informations sur les tableaux, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="36881-132">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="36881-133">Types de classes</span><span class="sxs-lookup"><span data-stu-id="36881-133">Class Types</span></span>  
 <span data-ttu-id="36881-134">Il n’existe aucun type de données unique comprenant toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="36881-134">There is no single data type comprising all classes.</span></span> <span data-ttu-id="36881-135">Même si une classe peut hériter d’une autre classe, chacune est un type de données distinct.</span><span class="sxs-lookup"><span data-stu-id="36881-135">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="36881-136">Plusieurs instances de la même classe sont du même type de données.</span><span class="sxs-lookup"><span data-stu-id="36881-136">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="36881-137">Si vous assignez une variable d’instance de classe vers un autre, non seulement font qu’ils ont les mêmes type de données, ils pointent vers la même instance de classe en mémoire.</span><span class="sxs-lookup"><span data-stu-id="36881-137">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="36881-138">Pour plus d’informations sur les classes, consultez [objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="36881-138">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36881-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36881-139">See Also</span></span>  
 [<span data-ttu-id="36881-140">Types de données</span><span class="sxs-lookup"><span data-stu-id="36881-140">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="36881-141">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="36881-141">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="36881-142">Types génériques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36881-142">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="36881-143">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="36881-143">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="36881-144">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36881-144">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="36881-145">Structures</span><span class="sxs-lookup"><span data-stu-id="36881-145">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="36881-146">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="36881-146">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="36881-147">Guide pratique : stocker plusieurs valeurs dans une variable</span><span class="sxs-lookup"><span data-stu-id="36881-147">How to: Hold More Than One Value in a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
