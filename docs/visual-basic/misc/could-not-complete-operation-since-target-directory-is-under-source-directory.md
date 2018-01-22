---
title: "Impossible d’achever l’opération, car le répertoire cible se situe sous le répertoire source"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a17877b2335ee010a97f0b522bd4c399867cd7d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a><span data-ttu-id="a55ad-102">Impossible d’achever l’opération, car le répertoire cible se situe sous le répertoire source</span><span class="sxs-lookup"><span data-stu-id="a55ad-102">Could not complete operation since target directory is under source directory</span></span>
<span data-ttu-id="a55ad-103">Une opération cyclique a échoué.</span><span class="sxs-lookup"><span data-stu-id="a55ad-103">A cyclic operation has failed.</span></span> <span data-ttu-id="a55ad-104">Les opérations cycliques se répètent et, par conséquent, ne peuvent pas s’achever.</span><span class="sxs-lookup"><span data-stu-id="a55ad-104">Cyclic operations cycle and therefore cannot complete.</span></span> <span data-ttu-id="a55ad-105">Par exemple, l’objet A peut essayer d’hériter de l’objet B qui hérite, à son tour, de l’objet A.</span><span class="sxs-lookup"><span data-stu-id="a55ad-105">For example, Object A may attempt to inherit from Object B, which in turn inherits from Object A.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a55ad-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="a55ad-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a55ad-107">Lors d’un héritage, vérifiez qu’il n’existe aucune référence cyclique.</span><span class="sxs-lookup"><span data-stu-id="a55ad-107">When inheriting, make sure that there are no cyclic references.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55ad-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a55ad-108">See Also</span></span>  
 [<span data-ttu-id="a55ad-109">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="a55ad-109">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="a55ad-110">Éléments fondamentaux du débogage : points d’arrêt</span><span class="sxs-lookup"><span data-stu-id="a55ad-110">Debugging Basics: Breakpoints</span></span>](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
