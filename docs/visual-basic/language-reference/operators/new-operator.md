---
title: "New, opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="873f7-102">New, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="873f7-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="873f7-103">Introduit un `New` clause pour créer une nouvelle instance de l’objet, spécifie une contrainte de constructeur sur un paramètre de type ou identifie une `Sub` procédure sous la forme d’un constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="873f7-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="873f7-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="873f7-104">Remarks</span></span>  
 <span data-ttu-id="873f7-105">Dans une déclaration ou une instruction d’assignation, un `New` clause doit spécifier une classe définie à partir de laquelle l’instance peut être créée.</span><span class="sxs-lookup"><span data-stu-id="873f7-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="873f7-106">Cela signifie que la classe doit exposer un ou plusieurs constructeurs accessibles par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="873f7-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="873f7-107">Vous pouvez utiliser un `New` clause dans une instruction de déclaration ou une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="873f7-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="873f7-108">Lorsque l’instruction s’exécute, il appelle le constructeur approprié de la classe spécifiée, en passant les arguments que vous avez fournies.</span><span class="sxs-lookup"><span data-stu-id="873f7-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="873f7-109">L’exemple suivant illustre cela en créant des instances d’un `Customer` classe qui possède deux constructeurs, qui ne prend aucun paramètre et une qui prend un paramètre de chaîne.</span><span class="sxs-lookup"><span data-stu-id="873f7-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="873f7-110">Étant donné que les tableaux sont des classes, `New` peut créer une nouvelle instance de tableau, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="873f7-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="873f7-111">Le common language runtime (CLR) lève une <xref:System.OutOfMemoryException> erreur si la mémoire est insuffisante pour créer la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="873f7-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="873f7-112">Le `New` est également utilisé dans les listes de paramètres de type pour spécifier que le type fourni doit exposer un constructeur sans paramètre accessible.</span><span class="sxs-lookup"><span data-stu-id="873f7-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="873f7-113">Pour plus d’informations sur les paramètres de type et les contraintes, consultez [Type liste](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="873f7-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="873f7-114">Pour créer une procédure de constructeur pour une classe, définissez le nom d’un `Sub` procédure pour le `New` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="873f7-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="873f7-115">Pour plus d’informations, consultez [durée de vie : comment les objets sont création et destruction](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="873f7-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="873f7-116">Le mot clé `New` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="873f7-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="873f7-117">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="873f7-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="873f7-118">Of</span><span class="sxs-lookup"><span data-stu-id="873f7-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="873f7-119">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="873f7-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="873f7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="873f7-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="873f7-121">Mots clés</span><span class="sxs-lookup"><span data-stu-id="873f7-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="873f7-122">Liste de types</span><span class="sxs-lookup"><span data-stu-id="873f7-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="873f7-123">Types génériques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="873f7-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="873f7-124">Durée de vie d’un objet : création et destruction des objets</span><span class="sxs-lookup"><span data-stu-id="873f7-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
