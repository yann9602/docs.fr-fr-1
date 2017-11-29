---
title: "checked (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords: checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a><span data-ttu-id="0516e-102">checked (référence C#)</span><span class="sxs-lookup"><span data-stu-id="0516e-102">checked (C# Reference)</span></span>
<span data-ttu-id="0516e-103">Le mot clé `checked` permet d’activer explicitement le contrôle de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.</span><span class="sxs-lookup"><span data-stu-id="0516e-103">The `checked` keyword is used to explicitly enable overflow checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="0516e-104">Par défaut, une expression qui contient uniquement des valeurs constantes provoque une erreur du compilateur si l’expression produit une valeur située en dehors de la plage du type de destination.</span><span class="sxs-lookup"><span data-stu-id="0516e-104">By default, an expression that contains only constant values causes a compiler error if the expression produces a value that is outside the range of the destination type.</span></span> <span data-ttu-id="0516e-105">Si l’expression contient une ou plusieurs valeurs non constantes, le compilateur ne détecte pas le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="0516e-105">If the expression contains one or more non-constant values, the compiler does not detect the overflow.</span></span> <span data-ttu-id="0516e-106">L’évaluation de l’expression assignée à `i2` dans l’exemple suivant ne provoque pas d’erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="0516e-106">Evaluating the expression assigned to `i2` in the following example does not cause a compiler error.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 <span data-ttu-id="0516e-107">Par défaut, ces expressions non constantes ne font pas l’objet d’une vérification d’un dépassement de capacité au moment de l’exécution et ne lèvent aucune exception de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="0516e-107">By default, these non-constant expressions are not checked for overflow at run time either, and they do not raise overflow exceptions.</span></span> <span data-ttu-id="0516e-108">L’exemple précédent affiche -2 147 483 639 comme somme de deux entiers positifs.</span><span class="sxs-lookup"><span data-stu-id="0516e-108">The previous example displays -2,147,483,639 as the sum of two positive integers.</span></span>  
  
 <span data-ttu-id="0516e-109">Le contrôle de dépassement de capacité peut être activé par les options du compilateur, la configuration de l’environnement ou l’utilisation du mot clé `checked`.</span><span class="sxs-lookup"><span data-stu-id="0516e-109">Overflow checking can be enabled by compiler options, environment configuration, or use of the `checked` keyword.</span></span> <span data-ttu-id="0516e-110">Les exemples suivants montrent comment utiliser une expression `checked` ou un bloc `checked` pour détecter le dépassement de capacité produit par la somme précédente au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0516e-110">The following examples demonstrate how to use a `checked` expression or a `checked` block to detect the overflow that is produced by the previous sum at run time.</span></span> <span data-ttu-id="0516e-111">Les deux exemples lèvent une exception de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="0516e-111">Both examples raise an overflow exception.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 <span data-ttu-id="0516e-112">Vous pouvez utiliser le mot clé [unchecked](../../../csharp/language-reference/keywords/unchecked.md) pour empêcher la vérification du dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="0516e-112">The [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword can be used to prevent overflow checking.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0516e-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="0516e-113">Example</span></span>  
 <span data-ttu-id="0516e-114">Cet exemple montre comment utiliser `checked` pour activer la vérification du dépassement de capacité au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0516e-114">This sample shows how to use `checked` to enable overflow checking at run time.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0516e-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="0516e-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0516e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0516e-116">See Also</span></span>  
 [<span data-ttu-id="0516e-117">Référence C#</span><span class="sxs-lookup"><span data-stu-id="0516e-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0516e-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="0516e-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0516e-119">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="0516e-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0516e-120">Checked et unchecked</span><span class="sxs-lookup"><span data-stu-id="0516e-120">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [<span data-ttu-id="0516e-121">unchecked</span><span class="sxs-lookup"><span data-stu-id="0516e-121">unchecked</span></span>](../../../csharp/language-reference/keywords/unchecked.md)
