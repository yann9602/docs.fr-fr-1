---
title: "Effectuer une sous-requête sur une opération de regroupement"
description: "Guide pratique pour effectuer une sous-requête sur une opération de regroupement."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: f638b8a679a15891d04e02f1597d6bf7934a9e74
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="2cf19-104">Effectuer une sous-requête sur une opération de regroupement</span><span class="sxs-lookup"><span data-stu-id="2cf19-104">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="2cf19-105">Cette rubrique présente deux façons de créer une requête qui organise les données sources en groupes et effectue ensuite une sous-requête sur chacun de ces groupes.</span><span class="sxs-lookup"><span data-stu-id="2cf19-105">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="2cf19-106">Dans chaque exemple, la technique de base consiste à regrouper les éléments sources en utilisant une *continuation* nommée `newGroup`, puis en créant une sous-requête sur `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="2cf19-106">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="2cf19-107">Cette sous-requête est exécutée sur chaque groupe créé par la requête externe.</span><span class="sxs-lookup"><span data-stu-id="2cf19-107">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="2cf19-108">Notez que, dans cet exemple particulier, le résultat final n’est pas un groupe, mais une séquence plate de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="2cf19-108">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="2cf19-109">Pour plus d’informations sur les regroupements, consultez [group, clause](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2cf19-109">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="2cf19-110">Pour plus d’informations sur les continuations, consultez [into](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="2cf19-110">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="2cf19-111">L’exemple suivant utilise une structure de données en mémoire comme source de données, mais les mêmes principes s’appliquent à tous les types de sources de données LINQ.</span><span class="sxs-lookup"><span data-stu-id="2cf19-111">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cf19-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cf19-112">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="2cf19-113">Cet exemple contient des références aux objets définis dans l’exemple de code qui est présenté dans [Interroger une collection d’objets](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="2cf19-113">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a><span data-ttu-id="2cf19-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cf19-114">See also</span></span>  
 [<span data-ttu-id="2cf19-115">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="2cf19-115">LINQ Query Expressions</span></span>](index.md)
