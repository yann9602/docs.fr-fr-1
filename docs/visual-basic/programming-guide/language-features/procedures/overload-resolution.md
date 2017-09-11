---
title: "Résolution de surcharge (Visual Basic) | Documents Microsoft"
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
- overload resolution
- procedures, overloading
- procedures, calling
- procedure overloading, overload resolution
- signatures, procedure
- overloads, resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
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
ms.openlocfilehash: a4f350af0f7d964df45974990991a2e94b26551e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="overload-resolution-visual-basic"></a><span data-ttu-id="a5600-102">Résolution de surcharge (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5600-102">Overload Resolution (Visual Basic)</span></span>
<span data-ttu-id="a5600-103">Lorsque le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur rencontre un appel à une procédure défini dans plusieurs versions surchargées, le compilateur doit décider de la surcharge à appeler.</span><span class="sxs-lookup"><span data-stu-id="a5600-103">When the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler encounters a call to a procedure that is defined in several overloaded versions, the compiler must decide which of the overloads to call.</span></span> <span data-ttu-id="a5600-104">Pour cela, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5600-104">It does this by performing the following steps:</span></span>  
  
1.  <span data-ttu-id="a5600-105">**Accessibilité.**</span><span class="sxs-lookup"><span data-stu-id="a5600-105">**Accessibility.**</span></span> <span data-ttu-id="a5600-106">Il élimine toute surcharge avec un niveau d’accès qui empêche le code appelant de l’appeler.</span><span class="sxs-lookup"><span data-stu-id="a5600-106">It eliminates any overload with an access level that prevents the calling code from calling it.</span></span>  
  
2.  <span data-ttu-id="a5600-107">**Nombre de paramètres.**</span><span class="sxs-lookup"><span data-stu-id="a5600-107">**Number of Parameters.**</span></span> <span data-ttu-id="a5600-108">Il élimine les surcharges qui définissent un nombre différent de paramètres que ceux spécifiés dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="a5600-108">It eliminates any overload that defines a different number of parameters than are supplied in the call.</span></span>  
  
3.  <span data-ttu-id="a5600-109">**Types de données de paramètre.**</span><span class="sxs-lookup"><span data-stu-id="a5600-109">**Parameter Data Types.**</span></span> <span data-ttu-id="a5600-110">Le compilateur donne la préférence de méthodes d’instance sur les méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="a5600-110">The compiler gives instance methods preference over extension methods.</span></span> <span data-ttu-id="a5600-111">Si n’importe quelle méthode d’instance est trouvée qui nécessite uniquement des conversions pour faire correspondre l’appel de procédure étendues, toutes les méthodes d’extension sont supprimées et le compilateur continue avec uniquement les candidats de méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="a5600-111">If any instance method is found that requires only widening conversions to match the procedure call, all extension methods are dropped and the compiler continues with only the instance method candidates.</span></span> <span data-ttu-id="a5600-112">Si aucune méthode d’instance de ce type n’est trouvée, il continue avec l’instance et les méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="a5600-112">If no such instance method is found, it continues with both instance and extension methods.</span></span>  
  
     <span data-ttu-id="a5600-113">Dans cette étape, il élimine les surcharges dont les types de données des arguments d’appel ne peut pas être convertis pour les types de paramètres définis dans la surcharge.</span><span class="sxs-lookup"><span data-stu-id="a5600-113">In this step, it eliminates any overload for which the data types of the calling arguments cannot be converted to the parameter types defined in the overload.</span></span>  
  
4.  <span data-ttu-id="a5600-114">**Conversions restrictives.**</span><span class="sxs-lookup"><span data-stu-id="a5600-114">**Narrowing Conversions.**</span></span> <span data-ttu-id="a5600-115">Il élimine les surcharges qui nécessitent une conversion restrictive parmi les types d’argument appelant pour les types de paramètres définis.</span><span class="sxs-lookup"><span data-stu-id="a5600-115">It eliminates any overload that requires a narrowing conversion from the calling argument types to the defined parameter types.</span></span> <span data-ttu-id="a5600-116">Cela est vrai que la vérification du type de commutateur ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `On` ou `Off`.</span><span class="sxs-lookup"><span data-stu-id="a5600-116">This is true whether the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On` or `Off`.</span></span>  
  
5.  <span data-ttu-id="a5600-117">**Moindre extension.**</span><span class="sxs-lookup"><span data-stu-id="a5600-117">**Least Widening.**</span></span> <span data-ttu-id="a5600-118">Le compilateur considère les surcharges restantes par paires.</span><span class="sxs-lookup"><span data-stu-id="a5600-118">The compiler considers the remaining overloads in pairs.</span></span> <span data-ttu-id="a5600-119">Pour chaque paire, il compare les types de données des paramètres définis.</span><span class="sxs-lookup"><span data-stu-id="a5600-119">For each pair, it compares the data types of the defined parameters.</span></span> <span data-ttu-id="a5600-120">Si les types dans une des surcharges de tous les élargir les types correspondants dans l’autre, le compilateur élimine la seconde.</span><span class="sxs-lookup"><span data-stu-id="a5600-120">If the types in one of the overloads all widen to the corresponding types in the other, the compiler eliminates the latter.</span></span> <span data-ttu-id="a5600-121">Autrement dit, il conserve la surcharge qui nécessite le moins importante.</span><span class="sxs-lookup"><span data-stu-id="a5600-121">That is, it retains the overload that requires the least amount of widening.</span></span>  
  
6.  <span data-ttu-id="a5600-122">**Candidat unique.**</span><span class="sxs-lookup"><span data-stu-id="a5600-122">**Single Candidate.**</span></span> <span data-ttu-id="a5600-123">Il continue à rassembler les surcharges par paires jusqu'à ce que la seule surcharge et il résout l’appel à cette surcharge.</span><span class="sxs-lookup"><span data-stu-id="a5600-123">It continues considering overloads in pairs until only one overload remains, and it resolves the call to that overload.</span></span> <span data-ttu-id="a5600-124">Si le compilateur ne peut pas réduire les surcharges vers un seul candidat, il génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="a5600-124">If the compiler cannot reduce the overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="a5600-125">L’illustration suivante montre le processus qui détermine un ensemble de versions surchargées à appeler.</span><span class="sxs-lookup"><span data-stu-id="a5600-125">The following illustration shows the process that determines which of a set of overloaded versions to call.</span></span>  
  
 <span data-ttu-id="a5600-126">![Diagramme de flux de processus de résolution de surcharge](./media/overloadres.gif "OverloadRes")</span><span class="sxs-lookup"><span data-stu-id="a5600-126">![Flow diagram of overload resolution process](./media/overloadres.gif "OverloadRes")</span></span>  
<span data-ttu-id="a5600-127">Résolution parmi des versions surchargées</span><span class="sxs-lookup"><span data-stu-id="a5600-127">Resolving among overloaded versions</span></span>  
  
 <span data-ttu-id="a5600-128">L’exemple suivant illustre ce processus de résolution de surcharge.</span><span class="sxs-lookup"><span data-stu-id="a5600-128">The following example illustrates this overload resolution process.</span></span>  
  
 <span data-ttu-id="a5600-129">[!code-vb[VbVbcnProcedures&#62;](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5600-129">[!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]</span></span>  
  
 <span data-ttu-id="a5600-130">[!code-vb[VbVbcnProcedures&#63;](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a5600-130">[!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]</span></span>  
  
 <span data-ttu-id="a5600-131">Dans le premier appel, le compilateur élimine la première surcharge parce que le type du premier argument (`Short`) restreint au type du paramètre correspondant (`Byte`).</span><span class="sxs-lookup"><span data-stu-id="a5600-131">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="a5600-132">Il élimine ensuite la troisième surcharge parce que chaque argument de type dans la deuxième surcharge (`Short` et `Single`) s’étend au type correspondant dans la troisième surcharge (`Integer` et `Single`).</span><span class="sxs-lookup"><span data-stu-id="a5600-132">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="a5600-133">La deuxième surcharge requérant une extension moins importante, donc le compilateur utilise pour l’appel.</span><span class="sxs-lookup"><span data-stu-id="a5600-133">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="a5600-134">Dans le deuxième appel, le compilateur ne peut pas supprimer les surcharges en fonction restrictives.</span><span class="sxs-lookup"><span data-stu-id="a5600-134">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="a5600-135">Il élimine la troisième surcharge pour la même raison que le premier appel, car il peut appeler la deuxième surcharge moyennant une extension moins importante des types d’arguments.</span><span class="sxs-lookup"><span data-stu-id="a5600-135">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="a5600-136">Toutefois, le compilateur ne peut pas résoudre entre les premier et deuxième surcharges.</span><span class="sxs-lookup"><span data-stu-id="a5600-136">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="a5600-137">Chacune possède un type de paramètre défini qui s’étend au type correspondant dans l’autre (`Byte` à `Short`, mais `Single` à `Double`).</span><span class="sxs-lookup"><span data-stu-id="a5600-137">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="a5600-138">Par conséquent, le compilateur génère une erreur de résolution de surcharge.</span><span class="sxs-lookup"><span data-stu-id="a5600-138">The compiler therefore generates an overload resolution error.</span></span>  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a><span data-ttu-id="a5600-139">Surchargé facultatif et Arguments ParamArray</span><span class="sxs-lookup"><span data-stu-id="a5600-139">Overloaded Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="a5600-140">Si deux surcharges d’une procédure ont des signatures identiques, mais que le dernier paramètre est déclaré [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) dans un et [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) dans l’autre, le compilateur résout un appel à cette procédure comme suit :</span><span class="sxs-lookup"><span data-stu-id="a5600-140">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure as follows:</span></span>  
  
|<span data-ttu-id="a5600-141">Si l’appel fournit le dernier argument comme</span><span class="sxs-lookup"><span data-stu-id="a5600-141">If the call supplies the last argument as</span></span>|<span data-ttu-id="a5600-142">Le compilateur résout l’appel vers la surcharge en déclarant le dernier argument comme</span><span class="sxs-lookup"><span data-stu-id="a5600-142">The compiler resolves the call to the overload declaring the last argument as</span></span>|  
|---|---|  
|<span data-ttu-id="a5600-143">Aucune valeur (argument omis)</span><span class="sxs-lookup"><span data-stu-id="a5600-143">No value (argument omitted)</span></span>|`Optional`|  
|<span data-ttu-id="a5600-144">Une valeur unique</span><span class="sxs-lookup"><span data-stu-id="a5600-144">A single value</span></span>|`Optional`|  
|<span data-ttu-id="a5600-145">Deux ou plusieurs valeurs dans une liste séparée par des virgules</span><span class="sxs-lookup"><span data-stu-id="a5600-145">Two or more values in a comma-separated list</span></span>|`ParamArray`|  
|<span data-ttu-id="a5600-146">Un tableau d’une longueur quelconque (y compris un tableau vide)</span><span class="sxs-lookup"><span data-stu-id="a5600-146">An array of any length (including an empty array)</span></span>|`ParamArray`|  
  
## <a name="see-also"></a><span data-ttu-id="a5600-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5600-147">See Also</span></span>  
 <span data-ttu-id="a5600-148">[Paramètres facultatifs](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-148">[Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="a5600-149"> [Tableaux de paramètres](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-149"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="a5600-150"> [Surcharge de procédure](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-150"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="a5600-151"> [Procédures de dépannage](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-151"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="a5600-152"> [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-152"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="a5600-153"> [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-153"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="a5600-154"> [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-154"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="a5600-155"> [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-155"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="a5600-156"> [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-156"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="a5600-157"> [Surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) </span><span class="sxs-lookup"><span data-stu-id="a5600-157"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) </span></span>  
<span data-ttu-id="a5600-158"> [Méthodes d’extension](./extension-methods.md)</span><span class="sxs-lookup"><span data-stu-id="a5600-158"> [Extension Methods](./extension-methods.md)</span></span>
