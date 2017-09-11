---
title: "Checked et Unchecked (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
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
ms.openlocfilehash: 744f59dbf7ee8370010ff76d4e9dde20490de403
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="87ca1-102">Checked et Unchecked (référence C#)</span><span class="sxs-lookup"><span data-stu-id="87ca1-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="87ca1-103">Les instructions C# peuvent s'exécuter dans un contexte vérifié (checked) ou non vérifié (unchecked).</span><span class="sxs-lookup"><span data-stu-id="87ca1-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="87ca1-104">Dans un contexte vérifié, un dépassement de capacité arithmétique lève une exception.</span><span class="sxs-lookup"><span data-stu-id="87ca1-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="87ca1-105">Dans un contexte non vérifié, un dépassement de capacité arithmétique et le résultat sont tronqués.</span><span class="sxs-lookup"><span data-stu-id="87ca1-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="87ca1-106">[checked](../../../csharp/language-reference/keywords/checked.md) Indique un contexte vérifié.</span><span class="sxs-lookup"><span data-stu-id="87ca1-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="87ca1-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Indique un contexte non vérifié.</span><span class="sxs-lookup"><span data-stu-id="87ca1-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="87ca1-108">Si ni `checked`, ni `unchecked` n'est spécifié, le contexte par défaut dépend de facteurs externes, notamment les options du compilateur.</span><span class="sxs-lookup"><span data-stu-id="87ca1-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="87ca1-109">Les opérations suivantes sont concernées par la vérification du dépassement de capacité :</span><span class="sxs-lookup"><span data-stu-id="87ca1-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="87ca1-110">Expressions utilisant les opérateurs prédéfinis suivants dans des types intégraux :</span><span class="sxs-lookup"><span data-stu-id="87ca1-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="87ca1-111">`++` `--` - (unaire)   `+` -   `*` `/`</span><span class="sxs-lookup"><span data-stu-id="87ca1-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="87ca1-112">Conversions numériques explicites entre types intégraux.</span><span class="sxs-lookup"><span data-stu-id="87ca1-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="87ca1-113">L’option de compilateur[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) vous permet d’indiquer le contexte vérifié ou non vérifié pour toutes les instructions arithmétiques entières qui ne figurent pas explicitement dans l’étendue d’un mot clé`checked` ou `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="87ca1-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ca1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87ca1-114">See Also</span></span>  
 <span data-ttu-id="87ca1-115">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="87ca1-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="87ca1-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="87ca1-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="87ca1-117">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="87ca1-117">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="87ca1-118">Mots clés d’instructions</span><span class="sxs-lookup"><span data-stu-id="87ca1-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)

