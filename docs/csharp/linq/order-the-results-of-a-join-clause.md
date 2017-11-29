---
title: "Classer les résultats d’une clause join"
description: "Guide pratique pour classer les résultats d’une clause join."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: a7458901-1201-4c25-b8d9-c04ca52e0eb9
ms.openlocfilehash: f948c18fb16a4f3ac02945b4a63583f1b01cad40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="order-the-results-of-a-join-clause"></a><span data-ttu-id="9523b-104">Classer les résultats d’une clause join</span><span class="sxs-lookup"><span data-stu-id="9523b-104">Order the results of a join clause</span></span>
<span data-ttu-id="9523b-105">Cet exemple montre comment classer les résultats d’une opération de jointure.</span><span class="sxs-lookup"><span data-stu-id="9523b-105">This example shows how to order the results of a join operation.</span></span> <span data-ttu-id="9523b-106">Notez que le classement est effectué après la jointure.</span><span class="sxs-lookup"><span data-stu-id="9523b-106">Note that the ordering is performed after the join.</span></span> <span data-ttu-id="9523b-107">Vous pouvez utiliser une clause `orderby` avec une ou plusieurs séquences sources avant la jointure, mais cette pratique est généralement déconseillée.</span><span class="sxs-lookup"><span data-stu-id="9523b-107">Although you can use an `orderby` clause with one or more of the source sequences before the join, generally we do not recommend it.</span></span> <span data-ttu-id="9523b-108">Certains fournisseurs LINQ ne conservent pas ce classement après la jointure.</span><span class="sxs-lookup"><span data-stu-id="9523b-108">Some LINQ providers might not preserve that ordering after the join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9523b-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="9523b-109">Example</span></span>  
 <span data-ttu-id="9523b-110">Cette requête crée une jointure groupée, puis trie les groupes en fonction de l’élément de catégorie, qui est encore dans la portée.</span><span class="sxs-lookup"><span data-stu-id="9523b-110">This query creates a group join, and then sorts the groups based on the category element, which is still in scope.</span></span> <span data-ttu-id="9523b-111">À l’intérieur de l’initialiseur de type anonyme, une sous-requête classe tous les éléments correspondants de la séquence de produits.</span><span class="sxs-lookup"><span data-stu-id="9523b-111">Inside the anonymous type initializer, a sub-query orders all the matching elements from the products sequence.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#81](../../../samples/snippets/csharp/concepts/linq/how-to-order-the-results-of-a-join-clause_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="9523b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9523b-112">See also</span></span>  
 [<span data-ttu-id="9523b-113">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="9523b-113">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="9523b-114">orderby, clause</span><span class="sxs-lookup"><span data-stu-id="9523b-114">orderby clause</span></span>](../language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="9523b-115">join, clause</span><span class="sxs-lookup"><span data-stu-id="9523b-115">join clause</span></span>](../language-reference/keywords/join-clause.md) 
