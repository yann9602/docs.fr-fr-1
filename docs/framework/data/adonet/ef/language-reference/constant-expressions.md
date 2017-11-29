---
title: Expressions constantes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 759805b2970aa760e4bce882789efbc947303573
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="constant-expressions"></a><span data-ttu-id="da030-102">Expressions constantes</span><span class="sxs-lookup"><span data-stu-id="da030-102">Constant Expressions</span></span>
<span data-ttu-id="da030-103">Une expression constante est composée d'une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="da030-103">A constant expression consists of a constant value.</span></span> <span data-ttu-id="da030-104">Les valeurs constantes sont converties directement en expressions d'arborescence de commandes constantes, sans aucune traduction sur le client.</span><span class="sxs-lookup"><span data-stu-id="da030-104">Constant values are directly converted to constant command tree expressions, without any translation on the client.</span></span> <span data-ttu-id="da030-105">Cela inclut les expressions qui génèrent une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="da030-105">This includes expressions that result in a constant value.</span></span> <span data-ttu-id="da030-106">Par conséquent, le comportement de la source de données doit être prévu pour toutes les expressions impliquant des constantes.</span><span class="sxs-lookup"><span data-stu-id="da030-106">Therefore, data source behavior should be expected for all expressions involving constants.</span></span> <span data-ttu-id="da030-107">Il peut en résulter un comportement différent du comportement CLR.</span><span class="sxs-lookup"><span data-stu-id="da030-107">This can result in behavior that differs from CLR behavior.</span></span>  
  
 <span data-ttu-id="da030-108">L'exemple suivant illustre une expression constante qui est évaluée sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="da030-108">The following example shows a constant expression that is evaluated on the server.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]<span data-ttu-id="da030-109"> ne prend pas en charge l'utilisation d'une classe d'utilisateur comme constante.</span><span class="sxs-lookup"><span data-stu-id="da030-109"> does not support using a user class as a constant.</span></span> <span data-ttu-id="da030-110">Toutefois, une référence de propriété sur une classe d’utilisateur est considérée comme une constante. Elle est donc convertie en expression constante d’arborescence de commandes et exécutée sur la source de données.</span><span class="sxs-lookup"><span data-stu-id="da030-110">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da030-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da030-111">See Also</span></span>  
 [<span data-ttu-id="da030-112">Expressions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="da030-112">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
