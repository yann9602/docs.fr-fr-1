---
title: "Comment : créer une variable qui ne change pas de valeur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="ff898-102">Comment : créer une variable qui ne change pas de valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff898-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="ff898-103">La notion d’une variable qui ne modifie pas sa valeur peut sembler être contradictoires.</span><span class="sxs-lookup"><span data-stu-id="ff898-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="ff898-104">Mais il existe des situations lorsqu’une constante n’est pas possible et il est utile de disposer d’une variable avec une valeur fixe.</span><span class="sxs-lookup"><span data-stu-id="ff898-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="ff898-105">Dans ce cas, vous pouvez définir une variable membre avec le [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="ff898-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="ff898-106">Vous ne pouvez pas utiliser le [instruction Const](../../../../visual-basic/language-reference/statements/const-statement.md) pour déclarer et assigner une valeur de constante dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="ff898-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="ff898-107">La `Const` instruction n’accepte pas le type de données que vous souhaitez utiliser</span><span class="sxs-lookup"><span data-stu-id="ff898-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="ff898-108">Vous ne connaissez pas la valeur au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="ff898-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="ff898-109">Vous ne parvenez pas à calculer la valeur constante au moment de la compilation</span><span class="sxs-lookup"><span data-stu-id="ff898-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="ff898-110">Pour créer une variable qui ne change pas de valeur</span><span class="sxs-lookup"><span data-stu-id="ff898-110">To create a variable that does not change in value</span></span>  
  
1.  <span data-ttu-id="ff898-111">Au niveau du module, déclarez une variable membre avec le [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)et incluent le [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="ff898-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="ff898-112">Vous pouvez spécifier `ReadOnly` uniquement sur une variable membre.</span><span class="sxs-lookup"><span data-stu-id="ff898-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="ff898-113">Cela signifie que vous devez définir la variable au niveau du module, en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="ff898-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2.  <span data-ttu-id="ff898-114">Si vous pouvez calculer la valeur dans une seule instruction au moment de la compilation, utilisez une clause d’initialisation dans le `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="ff898-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="ff898-115">Suivez les [en tant que](../../../../visual-basic/language-reference/statements/as-clause.md) clause avec un signe égal (`=`), suivi d’une expression.</span><span class="sxs-lookup"><span data-stu-id="ff898-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="ff898-116">Assurez-vous que le compilateur peut évaluer cette expression à une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="ff898-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="ff898-117">Vous pouvez affecter une valeur à une `ReadOnly` variable une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ff898-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="ff898-118">Une fois que vous procédez ainsi, aucun code n’est susceptible de changer sa valeur.</span><span class="sxs-lookup"><span data-stu-id="ff898-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="ff898-119">Si vous ne connaissez pas la valeur au moment de la compilation, ou ne peut pas calculer au moment de la compilation dans une seule instruction, vous pouvez l’affecter au moment de l’exécution dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="ff898-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="ff898-120">Pour ce faire, vous devez déclarer le `ReadOnly` variable au niveau de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="ff898-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="ff898-121">Dans le constructeur de cette classe ou structure, calculer la valeur fixe de la variable et affecter à la variable avant de retourner à partir du constructeur.</span><span class="sxs-lookup"><span data-stu-id="ff898-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff898-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff898-122">See Also</span></span>  
 [<span data-ttu-id="ff898-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="ff898-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="ff898-124">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="ff898-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
