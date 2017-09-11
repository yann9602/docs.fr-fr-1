---
title: "Procédures récursives (Visual Basic) | Documents Microsoft"
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
- Visual Basic code, procedures
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
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
ms.openlocfilehash: 5e4838bb14125dcfd27798acf0c196f351ba5b90
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="d5b60-102">Procédures récursives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5b60-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="d5b60-103">A *récursive* procédure est celle qui s’appelle elle-même.</span><span class="sxs-lookup"><span data-stu-id="d5b60-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="d5b60-104">En général, cela n’est pas le moyen le plus efficace pour écrire [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span><span class="sxs-lookup"><span data-stu-id="d5b60-104">In general, this is not the most effective way to write [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
 <span data-ttu-id="d5b60-105">La procédure suivante utilise la récursivité pour calculer la factorielle de son argument d’origine.</span><span class="sxs-lookup"><span data-stu-id="d5b60-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 <span data-ttu-id="d5b60-106">[!code-vb[VbVbcnProcedures&#51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d5b60-106">[!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]</span></span>  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="d5b60-107">Considérations sur les procédures récursives</span><span class="sxs-lookup"><span data-stu-id="d5b60-107">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="d5b60-108">**Conditions de limitation**.</span><span class="sxs-lookup"><span data-stu-id="d5b60-108">**Limiting Conditions**.</span></span> <span data-ttu-id="d5b60-109">Vous devez concevoir une procédure récursive à tester au moins une condition qui peut mettre fin à la récurrence, et vous devez également gérer le cas où aucune de ces conditions n’est satisfaite un nombre raisonnable d’appels récursifs.</span><span class="sxs-lookup"><span data-stu-id="d5b60-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="d5b60-110">Au moins une condition qui peut être satisfaite sans erreur, votre procédure s’exécute à un risque élevé d’exécution dans une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="d5b60-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="d5b60-111">**Utilisation de la mémoire**.</span><span class="sxs-lookup"><span data-stu-id="d5b60-111">**Memory Usage**.</span></span> <span data-ttu-id="d5b60-112">Votre application dispose d’une quantité limitée d’espace pour les variables locales.</span><span class="sxs-lookup"><span data-stu-id="d5b60-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="d5b60-113">Chaque fois qu’une procédure appelle elle-même, elle davantage d’espace utilise des copies supplémentaires de ses variables locales.</span><span class="sxs-lookup"><span data-stu-id="d5b60-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="d5b60-114">Si ce processus se poursuit indéfiniment, il provoque finalement un <xref:System.StackOverflowException>erreur.</xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="d5b60-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="d5b60-115">**L’efficacité**.</span><span class="sxs-lookup"><span data-stu-id="d5b60-115">**Efficiency**.</span></span> <span data-ttu-id="d5b60-116">Vous pouvez presque toujours remplacer une boucle de récurrence.</span><span class="sxs-lookup"><span data-stu-id="d5b60-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="d5b60-117">Une boucle n’a pas la surcharge de passer des arguments, initialiser le stockage supplémentaire et retourner des valeurs.</span><span class="sxs-lookup"><span data-stu-id="d5b60-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="d5b60-118">Votre performance peut être considérablement améliorée sans appels récurrents.</span><span class="sxs-lookup"><span data-stu-id="d5b60-118">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="d5b60-119">**Récurrence mutuelle**.</span><span class="sxs-lookup"><span data-stu-id="d5b60-119">**Mutual Recursion**.</span></span> <span data-ttu-id="d5b60-120">Vous pouvez observer une performance médiocre ou même une boucle infinie, si deux procédures s’appellent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="d5b60-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="d5b60-121">Ce type de conception présente les mêmes problèmes qu’une procédure récursive simple, mais il peut être difficile à détecter et à déboguer.</span><span class="sxs-lookup"><span data-stu-id="d5b60-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="d5b60-122">**Appel avec parenthèses**.</span><span class="sxs-lookup"><span data-stu-id="d5b60-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="d5b60-123">Lorsqu’un `Function` procédure appelle de manière récursive, vous devez suivre le nom de la procédure de parenthèses, même s’il n’existe aucune liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="d5b60-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="d5b60-124">Dans le cas contraire, le nom de fonction est utilisé en tant que représentant la valeur de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d5b60-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="d5b60-125">**Test**.</span><span class="sxs-lookup"><span data-stu-id="d5b60-125">**Testing**.</span></span> <span data-ttu-id="d5b60-126">Si vous écrivez une procédure récursive, vous devez la tester soigneusement pour vous assurer qu’il répond toujours à certaines conditions de limitation.</span><span class="sxs-lookup"><span data-stu-id="d5b60-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="d5b60-127">Vous devez également vous assurer que vous ne pouvez pas manquer de mémoire en raison d’un trop grand nombre d’appels récursive.</span><span class="sxs-lookup"><span data-stu-id="d5b60-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b60-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5b60-128">See Also</span></span>  
 <span data-ttu-id="d5b60-129"><xref:System.StackOverflowException></xref:System.StackOverflowException></span><span class="sxs-lookup"><span data-stu-id="d5b60-129"><xref:System.StackOverflowException></span></span>   
<span data-ttu-id="d5b60-130"> [Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-130"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="d5b60-131"> [Procédures Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-131"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="d5b60-132"> [Procédures Function](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-132"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="d5b60-133"> [Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-133"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="d5b60-134"> [Procédures d’opérateur](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-134"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="d5b60-135"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="d5b60-136"> [Surcharge de procédure](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="d5b60-137"> [Procédures de dépannage](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="d5b60-138"> [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="d5b60-138"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="d5b60-139"> [Dépannage des exceptions : System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span><span class="sxs-lookup"><span data-stu-id="d5b60-139"> [Troubleshooting Exceptions: System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)</span></span>
