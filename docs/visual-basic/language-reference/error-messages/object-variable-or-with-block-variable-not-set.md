---
title: "Variable objet ou variable bloc With non définie | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID91
dev_langs:
- VB
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4db2c827c3e77cfa6cc51132f0d647a58c93c769
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="object-variable-or-with-block-variable-not-set"></a><span data-ttu-id="7346a-102">Variable objet ou variable bloc With non définie</span><span class="sxs-lookup"><span data-stu-id="7346a-102">Object variable or With block variable not set</span></span>
<span data-ttu-id="7346a-103">Une variable d’objet non valide est référencée.</span><span class="sxs-lookup"><span data-stu-id="7346a-103">An invalid object variable is being referenced.</span></span>   <span data-ttu-id="7346a-104">Cette erreur peut se produire pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="7346a-104">This error can occur for several reasons:</span></span>  
  
-   <span data-ttu-id="7346a-105">Une variable a été déclarée sans spécification d’un type.</span><span class="sxs-lookup"><span data-stu-id="7346a-105">A variable was declared without specifying a type.</span></span> <span data-ttu-id="7346a-106">Si une variable est déclarée sans spécification d’un type, les valeurs par défaut pour le type `Object`.</span><span class="sxs-lookup"><span data-stu-id="7346a-106">If a variable is declared without specifying a type, it defaults to type `Object`.</span></span>  
  
     <span data-ttu-id="7346a-107">Par exemple, une variable déclarée avec `Dim x` sont de type `Object;` une variable déclarée avec `Dim x As String` sont de type `String`.</span><span class="sxs-lookup"><span data-stu-id="7346a-107">For example, a variable declared with `Dim x` would be of type `Object;` a variable declared with `Dim x As String` would be of type `String`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="7346a-108">Le `Option Strict` instruction n’autorise pas la saisie implicite qui résulte dans une `Object` type.</span><span class="sxs-lookup"><span data-stu-id="7346a-108">The `Option Strict` statement disallows implicit typing that results in an `Object` type.</span></span> <span data-ttu-id="7346a-109">Si vous omettez le type, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="7346a-109">If you omit the type, a compile-time error will occur.</span></span> <span data-ttu-id="7346a-110">Consultez la page [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7346a-110">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
-   <span data-ttu-id="7346a-111">Vous tentez de référencer un objet qui a été défini sur`Nothing`</span><span class="sxs-lookup"><span data-stu-id="7346a-111">You are attempting to reference an object that has been set to `Nothing`</span></span>  
  
     <span data-ttu-id="7346a-112">.</span><span class="sxs-lookup"><span data-stu-id="7346a-112">.</span></span>  
  
-   <span data-ttu-id="7346a-113">Vous tentez d’accéder à un élément d’une variable tableau qui n’a pas été déclaré correctement.</span><span class="sxs-lookup"><span data-stu-id="7346a-113">You are attempting to access an element of an array variable that wasn't properly declared.</span></span>  
  
     <span data-ttu-id="7346a-114">Par exemple, un tableau déclaré en tant que `products() As String` déclenche l’erreur si vous essayez de référencer un élément du tableau `products(3) = "Widget"`.</span><span class="sxs-lookup"><span data-stu-id="7346a-114">For example, an array declared as `products() As String` will trigger the error if you try to reference an element of the array `products(3) = "Widget"`.</span></span> <span data-ttu-id="7346a-115">Le tableau ne comporte aucun élément et est traité comme un objet.</span><span class="sxs-lookup"><span data-stu-id="7346a-115">The array has no elements and is treated as an object.</span></span>  
  
-   <span data-ttu-id="7346a-116">Vous tentez d’accéder au code dans un `With...End With` bloquer avant le bloc a été initialisé.</span><span class="sxs-lookup"><span data-stu-id="7346a-116">You are attempting to access code within a `With...End With` block before the block has been initialized.</span></span>   <span data-ttu-id="7346a-117">A `With...End With` doit être initialisé en exécutant le `With` point d’entrée l’instruction.</span><span class="sxs-lookup"><span data-stu-id="7346a-117">A `With...End With` block must be initialized by executing the `With` statement entry point.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7346a-118">Dans les versions antérieures de Visual Basic ou VBA cette erreur a été également déclenchée en affectant une valeur à une variable sans utiliser le `Set` (mot clé) (`x = "name"` au lieu de `Set x = "name"`).</span><span class="sxs-lookup"><span data-stu-id="7346a-118">In earlier versions of Visual Basic or VBA this error was also triggered by assigning a value to a variable without using the `Set` keyword (`x = "name"` instead of `Set x = "name"`).</span></span> <span data-ttu-id="7346a-119">Le `Set` mot clé n’est plus valide dans Visual Basic .net.</span><span class="sxs-lookup"><span data-stu-id="7346a-119">The `Set` keyword is no longer valid in Visual Basic .Net.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7346a-120">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="7346a-120">To correct this error</span></span>  
  
1.  <span data-ttu-id="7346a-121">Définissez `Option Strict` à `On` en ajoutant le code suivant au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="7346a-121">Set `Option Strict` to `On` by adding the following code to the beginning of the file:</span></span>  
  
```vb  
Option Strict On  
```  

     When you run the project, a compiler error will appear in the **Error List** for any variable that was specified without a type.  
  
2.  <span data-ttu-id="7346a-122">Si vous ne souhaitez pas activer `Option Strict`, recherchez le code de toutes les variables qui ont été spécifiées sans type (`Dim x` au lieu de `Dim x As String`) et ajoutez le type de destination à la déclaration.</span><span class="sxs-lookup"><span data-stu-id="7346a-122">If you don't want to enable `Option Strict`, search your code for any variables that were specified without a type (`Dim x` instead of `Dim x As String`) and add the intended type to the declaration.</span></span>  
  
3.  <span data-ttu-id="7346a-123">Assurez-vous que vous n’êtes pas référence à une variable objet qui a été définie sur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7346a-123">Make sure you aren't referring to  an object variable that has been set to `Nothing`.</span></span>  <span data-ttu-id="7346a-124">Recherchez le code pour le mot clé `Nothing`et modifier votre code pour que l’objet n’est pas défini sur `Nothing` jusqu'à ce qu’une fois que vous avez référencé il.</span><span class="sxs-lookup"><span data-stu-id="7346a-124">Search your code for the keyword `Nothing`, and revise your code so that the object isn't set to `Nothing` until after you have referenced it.</span></span>  
  
4.  <span data-ttu-id="7346a-125">Assurez-vous que toutes les variables tableau sont dimensionnés avant d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="7346a-125">Make sure that any array  variables are dimensioned before you access them.</span></span> <span data-ttu-id="7346a-126">Vous pouvez attribuer une dimension lorsque vous créez le tableau (`Dim x(5) As String` au lieu de `Dim x() As String`), ou utiliser le `ReDim` (mot clé) pour définir les dimensions du tableau avant tout d’abord accéder.</span><span class="sxs-lookup"><span data-stu-id="7346a-126">You can either assign a dimension when you first create the array (`Dim x(5) As String` instead of `Dim x() As String`), or use the `ReDim` keyword to set the dimensions of the array before you first access it.</span></span>  
  
5.  <span data-ttu-id="7346a-127">Assurez-vous que votre `With` est initialisé en exécutant le `With` point d’entrée l’instruction.</span><span class="sxs-lookup"><span data-stu-id="7346a-127">Make sure your `With` block is initialized by executing the `With` statement entry point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7346a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7346a-128">See Also</span></span>  
 <span data-ttu-id="7346a-129">[Déclaration des variables objets](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="7346a-129">[Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md) </span></span>  
<span data-ttu-id="7346a-130"> [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7346a-130"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="7346a-131"> [With...End With (instruction)](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="7346a-131"> [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
