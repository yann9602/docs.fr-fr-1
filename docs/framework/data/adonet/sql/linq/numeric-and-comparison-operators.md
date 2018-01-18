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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 56558e790b8aee300da0a75ade7c0ac451a0eca1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="numeric-and-comparison-operators"></a><span data-ttu-id="38bc6-102">Opérateurs de comparaison et opérateurs numériques</span><span class="sxs-lookup"><span data-stu-id="38bc6-102">Numeric and Comparison Operators</span></span>
<span data-ttu-id="38bc6-103">Les opérateurs arithmétiques et de comparaison fonctionnent conformément aux attentes dans le Common Language Runtime (CLR), à l'exception des points suivants :</span><span class="sxs-lookup"><span data-stu-id="38bc6-103">Arithmetic and comparison operators work as expected in the common language runtime (CLR) except as follows:</span></span>  
  
-   <span data-ttu-id="38bc6-104">SQL ne prend pas en charge l'opérateur modulo sur les nombres à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="38bc6-104">SQL does not support the modulus operator on floating-point numbers.</span></span>  
  
-   <span data-ttu-id="38bc6-105">SQL ne prend pas en charge l'arithmétique non contrôlée.</span><span class="sxs-lookup"><span data-stu-id="38bc6-105">SQL does not support unchecked arithmetic.</span></span>  
  
-   <span data-ttu-id="38bc6-106">Les opérateurs d'incrémentation et de décrémentation ne sont pas pris en charge car ils présentent des effets secondaires lorsqu'ils sont utilisés dans des expressions qui ne peuvent pas être répliquées dans SQL.</span><span class="sxs-lookup"><span data-stu-id="38bc6-106">Increment and decrement operators cause side-effects when you use them in expressions that cannot be replicated in SQL and are, therefore, not supported.</span></span>  
  
## <a name="supported-operators"></a><span data-ttu-id="38bc6-107">Opérateurs pris en charge</span><span class="sxs-lookup"><span data-stu-id="38bc6-107">Supported Operators</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="38bc6-108"> prend en charge les opérateurs suivants.</span><span class="sxs-lookup"><span data-stu-id="38bc6-108"> supports the following operators.</span></span>  
  
-   <span data-ttu-id="38bc6-109">Opérateurs arithmétiques de base :</span><span class="sxs-lookup"><span data-stu-id="38bc6-109">Basic arithmetic operators:</span></span>  
  
    -   `+`  
  
    -   <span data-ttu-id="38bc6-110">`-` (soustraction)</span><span class="sxs-lookup"><span data-stu-id="38bc6-110">`-` (subtraction)</span></span>  
  
    -   `*`  
  
    -   `/`  
  
    -   <span data-ttu-id="38bc6-111">Division d'entier Visual Basic (`\`)</span><span class="sxs-lookup"><span data-stu-id="38bc6-111">Visual Basic integer division (`\`)</span></span>  
  
    -   <span data-ttu-id="38bc6-112">`%` (`Mod` Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38bc6-112">`%` (Visual Basic `Mod`)</span></span>  
  
    -   `<<`  
  
    -   `>>`  
  
    -   <span data-ttu-id="38bc6-113">`-` (négation unaire)</span><span class="sxs-lookup"><span data-stu-id="38bc6-113">`-` (unary negation)</span></span>  
  
-   <span data-ttu-id="38bc6-114">Opérateurs de comparaison de base :</span><span class="sxs-lookup"><span data-stu-id="38bc6-114">Basic comparison operators:</span></span>  
  
    -   <span data-ttu-id="38bc6-115">`=` Visual Basic et `==` C#</span><span class="sxs-lookup"><span data-stu-id="38bc6-115">Visual Basic `=` and C# `==`</span></span>  
  
    -   <span data-ttu-id="38bc6-116">`<>` Visual Basic et `!=` C#</span><span class="sxs-lookup"><span data-stu-id="38bc6-116">Visual Basic `<>` and C# `!=`</span></span>  
  
    -   <span data-ttu-id="38bc6-117">Visual Basic `Is/IsNot`</span><span class="sxs-lookup"><span data-stu-id="38bc6-117">Visual Basic `Is/IsNot`</span></span>  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a><span data-ttu-id="38bc6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38bc6-118">See Also</span></span>  
 [<span data-ttu-id="38bc6-119">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="38bc6-119">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [<span data-ttu-id="38bc6-120">Opérateurs C#</span><span class="sxs-lookup"><span data-stu-id="38bc6-120">C# Operators</span></span>](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [<span data-ttu-id="38bc6-121">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="38bc6-121">Operators</span></span>](../../../../../visual-basic/language-reference/operators/index.md)
