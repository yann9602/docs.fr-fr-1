---
title: "Opérateurs de comparaison et opérateurs numériques"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b89555bc71d95291c096d2e694c315720cfb41c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="e95ad-102">Opérateurs de comparaison et opérateurs numériques</span><span class="sxs-lookup"><span data-stu-id="e95ad-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="e95ad-103">Les opérateurs arithmétiques et de comparaison fonctionnent conformément aux attentes dans le Common Language Runtime (CLR), à l'exception des points suivants :</span><span class="sxs-lookup"><span data-stu-id="e95ad-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="e95ad-104">SQL ne prend pas en charge l'opérateur modulo sur les nombres à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="e95ad-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="e95ad-105">SQL ne prend pas en charge l'arithmétique non contrôlée.</span><span class="sxs-lookup"><span data-stu-id="e95ad-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="e95ad-106">Les opérateurs d'incrémentation et de décrémentation ne sont pas pris en charge car ils présentent des effets secondaires lorsqu'ils sont utilisés dans des expressions qui ne peuvent pas être répliquées dans SQL.</span><span class="sxs-lookup"><span data-stu-id="e95ad-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="e95ad-107">Opérateurs pris en charge</span><span class="sxs-lookup"><span data-stu-id="e95ad-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e95ad-108"> prend en charge les opérateurs suivants.</span><span class="sxs-lookup"><span data-stu-id="e95ad-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="e95ad-109">Opérateurs arithmétiques de base :</span><span class="sxs-lookup"><span data-stu-id="e95ad-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="e95ad-110">`-` (soustraction)</span><span class="sxs-lookup"><span data-stu-id="e95ad-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="e95ad-111">Division d'entier Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="e95ad-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="e95ad-112">`%` (`Mod` Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e95ad-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="e95ad-113">`-` (négation unaire)</span><span class="sxs-lookup"><span data-stu-id="e95ad-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="e95ad-114">Opérateurs de comparaison de base :</span><span class="sxs-lookup"><span data-stu-id="e95ad-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="e95ad-115">`=` Visual Basic et `==` C#</span><span class="sxs-lookup"><span data-stu-id="e95ad-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="e95ad-116">`<>` Visual Basic et `!=` C#</span><span class="sxs-lookup"><span data-stu-id="e95ad-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="e95ad-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="e95ad-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="e95ad-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e95ad-118">See Also</span></span>  
 [<span data-ttu-id="e95ad-119">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="e95ad-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="e95ad-120">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="e95ad-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="e95ad-121">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="e95ad-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
