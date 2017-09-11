---
title: "Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e1e17ef2-68ff-4c26-b6e2-015668227fa5
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 30e994329234b8bd455f739694e50121bac63d5d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="query-expression-syntax-for-standard-query-operators-c"></a><span data-ttu-id="c0c3f-102">Syntaxe des expressions de requête pour les opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-102">Query Expression Syntax for Standard Query Operators (C#)</span></span>
<span data-ttu-id="c0c3f-103">Certains des opérateurs de requête standard les plus courants ont une syntaxe de mots clés C# dédiée qui permet de les appeler dans le cadre d’une *expression de requête*.</span><span class="sxs-lookup"><span data-stu-id="c0c3f-103">Some of the more frequently used standard query operators have dedicated C# language keyword syntax that enables them to be called as part of a *query expression*.</span></span> <span data-ttu-id="c0c3f-104">Une expression de requête est une façon différente et plus lisible d’exprimer une requête que son équivalent *fondé sur une méthode*.</span><span class="sxs-lookup"><span data-stu-id="c0c3f-104">A query expression is a different, more readable form of expressing a query than its *method-based*  equivalent.</span></span> <span data-ttu-id="c0c3f-105">Les clauses d'expression de requête sont traduites en appels aux méthodes de requête lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="c0c3f-105">Query expression clauses are translated into calls to the query methods at compile time.</span></span>  
  
## <a name="query-expression-syntax-table"></a><span data-ttu-id="c0c3f-106">Tableau de syntaxe des expressions de requête</span><span class="sxs-lookup"><span data-stu-id="c0c3f-106">Query Expression Syntax Table</span></span>  
 <span data-ttu-id="c0c3f-107">Le tableau ci-dessous répertorie les opérateurs de requête standard qui comportent des clauses d’expression de requête équivalentes.</span><span class="sxs-lookup"><span data-stu-id="c0c3f-107">The following table lists the standard query operators that have equivalent query expression clauses.</span></span>  
  
|<span data-ttu-id="c0c3f-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="c0c3f-108">Method</span></span>|<span data-ttu-id="c0c3f-109">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="c0c3f-109">C# Query Expression Syntax</span></span>|  
|------------|---------------------------------|  
|<xref:System.Linq.Enumerable.Cast%2A>|<span data-ttu-id="c0c3f-110">Utilisez une variable de portée explicitement typée, par exemple :</span><span class="sxs-lookup"><span data-stu-id="c0c3f-110">Use an explicitly typed range variable, for example:</span></span><br /><br /> `from int i in numbers`<br /><br /> <span data-ttu-id="c0c3f-111">(Pour plus d’informations, consultez [from, clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-111">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupBy%2A>|`group … by`<br /><br /> <span data-ttu-id="c0c3f-112">ou</span><span class="sxs-lookup"><span data-stu-id="c0c3f-112">-or-</span></span><br /><br /> `group … by … into …`<br /><br /> <span data-ttu-id="c0c3f-113">(Pour plus d’informations, consultez [group, clause](../../../../csharp/language-reference/keywords/group-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-113">(For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.GroupJoin%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|`join … in … on … equals … into …`<br /><br /> <span data-ttu-id="c0c3f-114">(Pour plus d’informations, consultez [join, clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-114">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|`join … in … on … equals …`<br /><br /> <span data-ttu-id="c0c3f-115">(Pour plus d’informations, consultez [join, clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-115">(For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby`<br /><br /> <span data-ttu-id="c0c3f-116">(Pour plus d’informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-116">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
<xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby … descending`<br /><br /> <span data-ttu-id="c0c3f-117">(Pour plus d’informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-117">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Select%2A>|`select`<br /><br /> <span data-ttu-id="c0c3f-118">(Pour plus d’informations, consultez [select, clause](../../../../csharp/language-reference/keywords/select-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-118">(For more information, see [select clause](../../../../csharp/language-reference/keywords/select-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.SelectMany%2A>|<span data-ttu-id="c0c3f-119">Plusieurs clauses `from`.</span><span class="sxs-lookup"><span data-stu-id="c0c3f-119">Multiple `from` clauses.</span></span><br /><br /> <span data-ttu-id="c0c3f-120">(Pour plus d’informations, consultez [from, clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-120">(For more information, see [from clause](../../../../csharp/language-reference/keywords/from-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, …`<br /><br /> <span data-ttu-id="c0c3f-121">(Pour plus d’informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-121">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>|`orderby …, … descending`<br /><br /> <span data-ttu-id="c0c3f-122">(Pour plus d’informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-122">(For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).)</span></span>|  
|<xref:System.Linq.Enumerable.Where%2A>|`where`<br /><br /> <span data-ttu-id="c0c3f-123">(Pour plus d’informations, consultez [where, clause](../../../../csharp/language-reference/keywords/where-clause.md).)</span><span class="sxs-lookup"><span data-stu-id="c0c3f-123">(For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0c3f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0c3f-124">See Also</span></span>  
 <span data-ttu-id="c0c3f-125"><xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="c0c3f-125"><xref:System.Linq.Enumerable></span></span>   
 <span data-ttu-id="c0c3f-126"><xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="c0c3f-126"><xref:System.Linq.Queryable></span></span>   
 <span data-ttu-id="c0c3f-127">[Présentation des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="c0c3f-127">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="c0c3f-128">Classification des opérateurs de requête standard en fonction de leur mode d’exécution</span><span class="sxs-lookup"><span data-stu-id="c0c3f-128">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)

