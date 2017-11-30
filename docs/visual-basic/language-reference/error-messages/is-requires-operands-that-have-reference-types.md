---
title: "&#39; est &#39; requiert des opérandes qui ont des types référence, mais cet opérande a le type de valeur &#39; &lt;typename&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords: BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28d017a566fdc1e55cb53ce907641d6bccfb354c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="662d6-102">&#39; est &#39; requiert des opérandes qui ont des types référence, mais cet opérande a le type de valeur &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="662d6-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="662d6-103">Le `Is` opérateur de comparaison détermine si deux variables objets font référence à la même instance.</span><span class="sxs-lookup"><span data-stu-id="662d6-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="662d6-104">Cette comparaison n’est pas définie pour les types valeur.</span><span class="sxs-lookup"><span data-stu-id="662d6-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="662d6-105">**ID d’erreur :** BC30020</span><span class="sxs-lookup"><span data-stu-id="662d6-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="662d6-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="662d6-106">To correct this error</span></span>  
  
-   <span data-ttu-id="662d6-107">Utilisez l’opérateur de comparaison arithmétique approprié ou `Like` pour comparer deux types valeur.</span><span class="sxs-lookup"><span data-stu-id="662d6-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662d6-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="662d6-108">See Also</span></span>  
 [<span data-ttu-id="662d6-109">Is (opérateur)</span><span class="sxs-lookup"><span data-stu-id="662d6-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="662d6-110">Like (opérateur)</span><span class="sxs-lookup"><span data-stu-id="662d6-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)  
 [<span data-ttu-id="662d6-111">Opérateurs de comparaison</span><span class="sxs-lookup"><span data-stu-id="662d6-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
