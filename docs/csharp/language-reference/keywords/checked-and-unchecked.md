---
title: "Checked et Unchecked (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="b2a76-102">Checked et Unchecked (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b2a76-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="b2a76-103">Les instructions C# peuvent s'exécuter dans un contexte vérifié (checked) ou non vérifié (unchecked).</span><span class="sxs-lookup"><span data-stu-id="b2a76-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="b2a76-104">Dans un contexte vérifié, un dépassement de capacité arithmétique lève une exception.</span><span class="sxs-lookup"><span data-stu-id="b2a76-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="b2a76-105">Dans un contexte non vérifié, un dépassement de capacité arithmétique et le résultat sont tronqués.</span><span class="sxs-lookup"><span data-stu-id="b2a76-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="b2a76-106">[checked](../../../csharp/language-reference/keywords/checked.md) Indique un contexte vérifié.</span><span class="sxs-lookup"><span data-stu-id="b2a76-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="b2a76-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Indique un contexte non vérifié.</span><span class="sxs-lookup"><span data-stu-id="b2a76-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="b2a76-108">Si ni `checked`, ni `unchecked` n'est spécifié, le contexte par défaut dépend de facteurs externes, notamment les options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="b2a76-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="b2a76-109">Les opérations suivantes sont concernées par la vérification du dépassement de capacité :</span><span class="sxs-lookup"><span data-stu-id="b2a76-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="b2a76-110">Expressions utilisant les opérateurs prédéfinis suivants dans des types intégraux :</span><span class="sxs-lookup"><span data-stu-id="b2a76-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="b2a76-111">`++` `--` - (unaire)   `+` -   `*` `/`</span><span class="sxs-lookup"><span data-stu-id="b2a76-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="b2a76-112">Conversions numériques explicites entre types intégraux.</span><span class="sxs-lookup"><span data-stu-id="b2a76-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="b2a76-113">L’option de compilateur[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) vous permet d’indiquer le contexte vérifié ou non vérifié pour toutes les instructions arithmétiques entières qui ne figurent pas explicitement dans l’étendue d’un mot clé`checked` ou `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="b2a76-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a76-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2a76-114">See Also</span></span>  
 [<span data-ttu-id="b2a76-115">Référence C#</span><span class="sxs-lookup"><span data-stu-id="b2a76-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b2a76-116">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b2a76-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b2a76-117">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="b2a76-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="b2a76-118">Mots clés d’instructions</span><span class="sxs-lookup"><span data-stu-id="b2a76-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)
