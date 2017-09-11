---
title: "Effectuer une sous-requête sur une opération de regroupement"
description: "Guide pratique pour effectuer une sous-requête sur une opération de regroupement."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 68acc07e0c33d042123d3cd403a73d58a7c3d245
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="bd917-104">Effectuer une sous-requête sur une opération de regroupement</span><span class="sxs-lookup"><span data-stu-id="bd917-104">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="bd917-105">Cette rubrique présente deux façons de créer une requête qui organise les données sources en groupes et effectue ensuite une sous-requête sur chacun de ces groupes.</span><span class="sxs-lookup"><span data-stu-id="bd917-105">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="bd917-106">Dans chaque exemple, la technique de base consiste à regrouper les éléments sources en utilisant une *continuation* nommée `newGroup`, puis en créant une sous-requête sur `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="bd917-106">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="bd917-107">Cette sous-requête est exécutée sur chaque groupe créé par la requête externe.</span><span class="sxs-lookup"><span data-stu-id="bd917-107">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="bd917-108">Notez que, dans cet exemple particulier, le résultat final n’est pas un groupe, mais une séquence plate de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="bd917-108">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="bd917-109">Pour plus d’informations sur les regroupements, consultez [group, clause](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bd917-109">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="bd917-110">Pour plus d’informations sur les continuations, consultez [into](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="bd917-110">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="bd917-111">L’exemple suivant utilise une structure de données en mémoire comme source de données, mais les mêmes principes s’appliquent à tous les types de sources de données LINQ.</span><span class="sxs-lookup"><span data-stu-id="bd917-111">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd917-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd917-112">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="bd917-113">Cet exemple contient des références aux objets définis dans l’exemple de code qui est présenté dans [Interroger une collection d’objets](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="bd917-113">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 <span data-ttu-id="bd917-114">[!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bd917-114">[!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]</span></span>  
   
## <a name="see-also"></a><span data-ttu-id="bd917-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd917-115">See also</span></span>  
 [<span data-ttu-id="bd917-116">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="bd917-116">LINQ Query Expressions</span></span>](index.md)

