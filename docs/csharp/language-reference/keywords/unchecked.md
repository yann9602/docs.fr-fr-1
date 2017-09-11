---
title: "unchecked (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
dev_langs:
- CSharp
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 5878a2412e6c85da85b1a3b8c2a8255b51e67137
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="unchecked-c-reference"></a><span data-ttu-id="b258e-102">unchecked (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b258e-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="b258e-103">Le mot clé `unchecked` permet de supprimer le contrôle de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.</span><span class="sxs-lookup"><span data-stu-id="b258e-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="b258e-104">Dans un contexte non vérifié (unchecked), si une expression produit une valeur située hors de la plage du type de destination, le dépassement de capacité n’est pas signalé.</span><span class="sxs-lookup"><span data-stu-id="b258e-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="b258e-105">Par exemple, comme le calcul dans l’exemple suivant s’effectue dans un bloc ou une expression `unchecked`, le fait que le résultat est trop grand pour un entier est ignoré et `int1` se voit assigner la valeur -2,147,483,639.</span><span class="sxs-lookup"><span data-stu-id="b258e-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 <span data-ttu-id="b258e-106">[!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b258e-106">[!code-cs[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]</span></span>  
  
 <span data-ttu-id="b258e-107">Si l’environnement `unchecked` est supprimé, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="b258e-107">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="b258e-108">Le dépassement de capacité peut être détecté au moment de la compilation, car tous les termes de l’expression sont des constantes.</span><span class="sxs-lookup"><span data-stu-id="b258e-108">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="b258e-109">Les expressions qui contiennent des termes non constants sont non vérifiées par défaut au moment de la compilation et de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b258e-109">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="b258e-110">Consultez [checked](../../../csharp/language-reference/keywords/checked.md) pour plus d’informations sur l’activation d’un environnement vérifié (checked).</span><span class="sxs-lookup"><span data-stu-id="b258e-110">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="b258e-111">Étant donné que la vérification de dépassement de capacité prend du temps, l’utilisation de code non vérifié dans les situations où il n’existe aucun danger de dépassement de capacité peut améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="b258e-111">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="b258e-112">Toutefois, si un dépassement de capacité est possible, il convient d’utiliser un environnement vérifié (checked).</span><span class="sxs-lookup"><span data-stu-id="b258e-112">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b258e-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="b258e-113">Example</span></span>  
 <span data-ttu-id="b258e-114">L’exemple de code suivant montre comment utiliser le mot clé `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="b258e-114">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 <span data-ttu-id="b258e-115">[!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b258e-115">[!code-cs[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b258e-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b258e-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b258e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b258e-117">See Also</span></span>  
 <span data-ttu-id="b258e-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b258e-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b258e-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b258e-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b258e-120">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b258e-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b258e-121">[Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) </span><span class="sxs-lookup"><span data-stu-id="b258e-121">[Checked and Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) </span></span>  
 [<span data-ttu-id="b258e-122">checked</span><span class="sxs-lookup"><span data-stu-id="b258e-122">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)

