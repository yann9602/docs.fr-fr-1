---
title: "Variable de portée &lt;variable&gt; masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords: BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="77af0-102">Variable de portée &lt;variable&gt; masque une variable dans un bloc englobant, une variable de portée précédemment définie ou une variable déclarée implicitement dans une expression de requête</span><span class="sxs-lookup"><span data-stu-id="77af0-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="77af0-103">Un nom de variable de plage spécifié dans un `Select`, `From`, `Aggregate`, ou `Let` clause duplique le nom d’une variable de portée spécifié précédemment dans la requête ou le nom d’une variable qui est déclarée implicitement par la requête, par exemple un nom de champ ou le nom d’une fonction d’agrégation.</span><span class="sxs-lookup"><span data-stu-id="77af0-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="77af0-104">**ID d’erreur :** BC36633</span><span class="sxs-lookup"><span data-stu-id="77af0-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="77af0-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="77af0-105">To correct this error</span></span>  
  
-   <span data-ttu-id="77af0-106">Assurez-vous que toutes les variables de plage dans une étendue de requête particulière ont des noms uniques.</span><span class="sxs-lookup"><span data-stu-id="77af0-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="77af0-107">Vous pouvez placer une requête entre parenthèses pour garantir que les requêtes imbriquées ont une étendue unique.</span><span class="sxs-lookup"><span data-stu-id="77af0-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77af0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77af0-108">See Also</span></span>  
 [<span data-ttu-id="77af0-109">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77af0-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="77af0-110">From (clause)</span><span class="sxs-lookup"><span data-stu-id="77af0-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="77af0-111">Let (clause)</span><span class="sxs-lookup"><span data-stu-id="77af0-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="77af0-112">Aggregate (clause)</span><span class="sxs-lookup"><span data-stu-id="77af0-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="77af0-113">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="77af0-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
