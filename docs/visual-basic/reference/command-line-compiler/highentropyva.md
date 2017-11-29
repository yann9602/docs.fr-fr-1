---
title: /highentropyva (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55568808bb94f98ce7a20016fc5a2a0a2ef23a38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="highentropyva-visual-basic"></a><span data-ttu-id="7538b-102">/highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7538b-102">/highentropyva (Visual Basic)</span></span>
<span data-ttu-id="7538b-103">Indique si un exécutable 64 bits ou qui est marquée par le [/Platform : anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) option du compilateur prend en charge la randomisation du format de mise en page espace adresse (ASLR) de forte entropie.</span><span class="sxs-lookup"><span data-stu-id="7538b-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7538b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7538b-104">Syntax</span></span>  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7538b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7538b-105">Arguments</span></span>  
 <span data-ttu-id="7538b-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7538b-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="7538b-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7538b-107">Optional.</span></span> <span data-ttu-id="7538b-108">L’option est désactivée par défaut ou si vous spécifiez `/highentropyva-`.</span><span class="sxs-lookup"><span data-stu-id="7538b-108">The option is off by default or if you specify `/highentropyva-`.</span></span> <span data-ttu-id="7538b-109">L’option est activée si vous spécifiez `/highentropyva` ou `/highentropyva+`.</span><span class="sxs-lookup"><span data-stu-id="7538b-109">The option is on if you specify `/highentropyva` or `/highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7538b-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="7538b-110">Remarks</span></span>  
 <span data-ttu-id="7538b-111">Si vous spécifiez cette option, les versions compatibles du noyau Windows peuvent utiliser un degré d’entropie lorsque le noyau rend aléatoire la disposition de l’espace adresse d’un processus dans le cadre de l’ASLR.</span><span class="sxs-lookup"><span data-stu-id="7538b-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="7538b-112">Si le noyau utilise un degré d’entropie, un plus grand nombre d’adresses peut être alloué à des régions de mémoire telles que les piles et de segments de mémoire.</span><span class="sxs-lookup"><span data-stu-id="7538b-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="7538b-113">Par conséquent, il est plus difficile de deviner l’emplacement d’une zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="7538b-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="7538b-114">Lorsque l’option est activée, l’exécutable cible et tous les modules sur dont il dépend doit être en mesure de gérer les valeurs de pointeur qui sont supérieures à 4 gigaoctets (Go) lorsque ces modules sont exécutent en tant que processus 64 bits.</span><span class="sxs-lookup"><span data-stu-id="7538b-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7538b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7538b-115">See Also</span></span>  
 [<span data-ttu-id="7538b-116">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7538b-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7538b-117">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="7538b-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
