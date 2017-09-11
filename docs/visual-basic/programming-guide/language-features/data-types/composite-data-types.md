---
title: "Types de données composites (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5f0c6215ce45d724a7b5c8c4f8e34ea27bce8fe4
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="74e9f-102">Types de données composites (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74e9f-102">Composite Data Types (Visual Basic)</span></span>
<span data-ttu-id="74e9f-103">Outre les types de données élémentaires [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit, vous pouvez assembler des éléments de différents types pour créer *types de données composites* tels que des structures, des tableaux et des classes.</span><span class="sxs-lookup"><span data-stu-id="74e9f-103">In addition to the elementary data types [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="74e9f-104">Vous pouvez créer des types de données composites à partir des types élémentaires et d’autres types composites.</span><span class="sxs-lookup"><span data-stu-id="74e9f-104">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="74e9f-105">Par exemple, vous pouvez définir un tableau d’éléments de structure ou une structure avec des membres de tableau.</span><span class="sxs-lookup"><span data-stu-id="74e9f-105">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="74e9f-106">Types de données</span><span class="sxs-lookup"><span data-stu-id="74e9f-106">Data Types</span></span>  
 <span data-ttu-id="74e9f-107">Un type composite diffère du type de données d’un de ses composants.</span><span class="sxs-lookup"><span data-stu-id="74e9f-107">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="74e9f-108">Par exemple, un tableau de `Integer` éléments n’est pas de la `Integer` type de données.</span><span class="sxs-lookup"><span data-stu-id="74e9f-108">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="74e9f-109">Un type de données de tableau est représenté normalement à l’aide du type d’élément, parenthèses et des virgules si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="74e9f-109">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="74e9f-110">Par exemple, un tableau unidimensionnel de `String` éléments est représenté en tant que `String()`, un tableau à deux dimensions de `Boolean` éléments est représenté en tant que `Boolean(,)`.</span><span class="sxs-lookup"><span data-stu-id="74e9f-110">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="74e9f-111">Types de structure</span><span class="sxs-lookup"><span data-stu-id="74e9f-111">Structure Types</span></span>  
 <span data-ttu-id="74e9f-112">Il n’existe aucun type de données unique comprenant toutes les structures.</span><span class="sxs-lookup"><span data-stu-id="74e9f-112">There is no single data type comprising all structures.</span></span> <span data-ttu-id="74e9f-113">Au lieu de cela, chaque définition d’une structure représente un type de données unique, même si deux structures définissent des éléments identiques dans le même ordre.</span><span class="sxs-lookup"><span data-stu-id="74e9f-113">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="74e9f-114">Toutefois, si vous créez deux ou plusieurs instances de la même structure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les considère comme du même type de données.</span><span class="sxs-lookup"><span data-stu-id="74e9f-114">However, if you create two or more instances of the same structure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considers them to be of the same data type.</span></span>  
  
## <a name="array-types"></a><span data-ttu-id="74e9f-115">Types tableau</span><span class="sxs-lookup"><span data-stu-id="74e9f-115">Array Types</span></span>  
 <span data-ttu-id="74e9f-116">Il n’existe aucun type de données englobant tous les tableaux.</span><span class="sxs-lookup"><span data-stu-id="74e9f-116">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="74e9f-117">Le type de données d’une instance particulière d’un tableau est déterminé par le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="74e9f-117">The data type of a particular instance of an array is determined by the following:</span></span>  
  
-   <span data-ttu-id="74e9f-118">Le fait d’être un tableau</span><span class="sxs-lookup"><span data-stu-id="74e9f-118">The fact of being an array</span></span>  
  
-   <span data-ttu-id="74e9f-119">Le rang (nombre de dimensions) du tableau</span><span class="sxs-lookup"><span data-stu-id="74e9f-119">The rank (number of dimensions) of the array</span></span>  
  
-   <span data-ttu-id="74e9f-120">Le type d’élément du tableau</span><span class="sxs-lookup"><span data-stu-id="74e9f-120">The element type of the array</span></span>  
  
 <span data-ttu-id="74e9f-121">En particulier, la longueur d’une dimension donnée n’est pas partie du type de données de l’instance.</span><span class="sxs-lookup"><span data-stu-id="74e9f-121">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="74e9f-122">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="74e9f-122">The following example illustrates this.</span></span>  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="74e9f-123">Dans l’exemple précédent, les variables tableau `arrayA` et `arrayB` sont considérés comme étant du même type de données : `Byte()` , même si elles sont initialisées avec des longueurs différentes.</span><span class="sxs-lookup"><span data-stu-id="74e9f-123">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="74e9f-124">Variables `arrayB` et `arrayC` ne sont pas du même type car leurs types d’éléments sont différents.</span><span class="sxs-lookup"><span data-stu-id="74e9f-124">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="74e9f-125">Variables `arrayC` et `arrayD` ne sont pas du même type car leurs rangs sont différents.</span><span class="sxs-lookup"><span data-stu-id="74e9f-125">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="74e9f-126">Variables `arrayD` et `arrayE` ont le même type — `Short(,)` , car leurs rangs et types d’élément sont identiques, même si `arrayD` n’est pas encore initialisé.</span><span class="sxs-lookup"><span data-stu-id="74e9f-126">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="74e9f-127">Pour plus d’informations sur les tableaux, consultez [tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="74e9f-127">For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="74e9f-128">Types de classes</span><span class="sxs-lookup"><span data-stu-id="74e9f-128">Class Types</span></span>  
 <span data-ttu-id="74e9f-129">Il n’existe aucun type de données unique comprenant toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="74e9f-129">There is no single data type comprising all classes.</span></span> <span data-ttu-id="74e9f-130">Bien qu’une classe peut hériter d’une autre classe, chacune est un type de données distinct.</span><span class="sxs-lookup"><span data-stu-id="74e9f-130">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="74e9f-131">Plusieurs instances de la même classe sont du même type de données.</span><span class="sxs-lookup"><span data-stu-id="74e9f-131">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="74e9f-132">Si vous assignez une variable d’instance de classe à une autre, non seulement font qu’ils ont les mêmes type de données, ils pointent vers la même instance de classe en mémoire.</span><span class="sxs-lookup"><span data-stu-id="74e9f-132">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="74e9f-133">Pour plus d’informations sur les classes, consultez [objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span><span class="sxs-lookup"><span data-stu-id="74e9f-133">For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e9f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74e9f-134">See Also</span></span>  
 <span data-ttu-id="74e9f-135">[Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="74e9f-135">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="74e9f-136"> [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="74e9f-136"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="74e9f-137"> [Types génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="74e9f-137"> [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="74e9f-138"> [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="74e9f-138"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="74e9f-139"> [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="74e9f-139"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="74e9f-140"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="74e9f-140"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="74e9f-141"> [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="74e9f-141"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="74e9f-142"> [Guide pratique : stocker plusieurs valeurs dans une variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span><span class="sxs-lookup"><span data-stu-id="74e9f-142"> [How to: Hold More Than One Value in a Variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)</span></span>
