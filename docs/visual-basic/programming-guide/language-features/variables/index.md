---
title: Variables en Visual Basic
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2fdc670bf4f17000809e75e32c32edb39abf0fed
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="dcfe5-102">Variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dcfe5-102">Variables in Visual Basic</span></span>
<span data-ttu-id="dcfe5-103">Il est souvent nécessaire de stocker des valeurs lors de l’exécution de calculs avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dcfe5-103">You often have to store values when you perform calculations with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="dcfe5-104">Par exemple, vous pouvez être amené à calculer plusieurs valeurs, à les comparer et à effectuer différentes opérations sur ces valeurs, en fonction du résultat de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="dcfe5-105">Vous devez conserver les valeurs si vous souhaitez les comparer.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="dcfe5-106">Utilisation</span><span class="sxs-lookup"><span data-stu-id="dcfe5-106">Usage</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="dcfe5-107">, comme la plupart des langages de programmation, utilise des variables pour le stockage des valeurs.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-107">, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="dcfe5-108">Une *variable* a un nom (le mot que vous utilisez pour faire référence à la valeur que la variable contient).</span><span class="sxs-lookup"><span data-stu-id="dcfe5-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="dcfe5-109">Une variable a également un type de données (lequel détermine le genre des données que la variable peut stocker).</span><span class="sxs-lookup"><span data-stu-id="dcfe5-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="dcfe5-110">Une variable peut représenter un tableau si elle doit stocker un ensemble indexé d’éléments de données étroitement liés.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="dcfe5-111">L’inférence de type de variable locale vous permet de déclarer des variables sans déclarer explicitement un type de données.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="dcfe5-112">À la place, le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="dcfe5-113">Pour plus d’informations, consultez [Inférence de type de variable locale](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) et [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dcfe5-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="dcfe5-114">Assignation de valeurs</span><span class="sxs-lookup"><span data-stu-id="dcfe5-114">Assigning Values</span></span>  
 <span data-ttu-id="dcfe5-115">Vous utilisez des instructions d’assignation pour effectuer des calculs et assigner le résultat à une variable, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 <span data-ttu-id="dcfe5-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="dcfe5-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcfe5-117">Dans cet exemple, le signe égal (`=`) représente un opérateur d’assignation, et non un opérateur d’égalité.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-117">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="dcfe5-118">La valeur est assignée à la variable `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-118">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="dcfe5-119">Pour plus d’informations, consultez [Guide pratique pour placer des données dans et en dehors d’une variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="dcfe5-119">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="dcfe5-120">Variables et propriétés</span><span class="sxs-lookup"><span data-stu-id="dcfe5-120">Variables and Properties</span></span>  
 <span data-ttu-id="dcfe5-121">À l’instar d’une variable, une *propriété* représente une valeur à laquelle vous pouvez accéder.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-121">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="dcfe5-122">Toutefois, elle est plus complexe qu’une variable.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-122">However, it is more complex than a variable.</span></span> <span data-ttu-id="dcfe5-123">Une propriété utilise des blocs de code qui contrôlent la définition et la récupération de sa valeur.</span><span class="sxs-lookup"><span data-stu-id="dcfe5-123">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="dcfe5-124">Pour plus d’informations, consultez [Différences entre les propriétés et les variables en Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="dcfe5-124">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcfe5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcfe5-125">See Also</span></span>  
 <span data-ttu-id="dcfe5-126">[Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="dcfe5-126">[Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
 <span data-ttu-id="dcfe5-127">[Variables objet](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="dcfe5-127">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
 <span data-ttu-id="dcfe5-128">[Dépannage des variables](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="dcfe5-128">[Troubleshooting Variables](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span></span>  
 <span data-ttu-id="dcfe5-129">[Guide pratique pour placer des données dans et en dehors d’une variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="dcfe5-129">[How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span></span>  
 <span data-ttu-id="dcfe5-130">[Différences entre les propriétés et les variables en Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="dcfe5-130">[Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span></span>  
 [<span data-ttu-id="dcfe5-131">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="dcfe5-131">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

