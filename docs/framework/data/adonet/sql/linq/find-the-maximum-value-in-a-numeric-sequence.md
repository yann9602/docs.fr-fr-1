---
title: "Comment : rechercher la valeur maximale dans une séquence numérique"
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
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 387fe8db55da337b970bbac0e6e046b43433b482
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a><span data-ttu-id="e7fdc-102">Comment : rechercher la valeur maximale dans une séquence numérique</span><span class="sxs-lookup"><span data-stu-id="e7fdc-102">Find the Maximum Value in a Numeric Sequence</span></span>
<span data-ttu-id="e7fdc-103">Utilisez l'opérateur <xref:System.Linq.Enumerable.Max%2A> pour rechercher la valeur la plus élevée dans une séquence de valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="e7fdc-103">Use the <xref:System.Linq.Enumerable.Max%2A> operator to find the highest value in a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7fdc-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7fdc-104">Example</span></span>  
 <span data-ttu-id="e7fdc-105">L'exemple suivant recherche la date la plus récente d'embauche parmi tous les employés.</span><span class="sxs-lookup"><span data-stu-id="e7fdc-105">The following example finds the latest date of hire for any employee.</span></span>  
  
 <span data-ttu-id="e7fdc-106">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `11/15/1994 12:00:00 AM`.</span><span class="sxs-lookup"><span data-stu-id="e7fdc-106">If you run this query against the sample Northwind database, the output is: `11/15/1994 12:00:00 AM`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="e7fdc-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7fdc-107">Example</span></span>  
 <span data-ttu-id="e7fdc-108">L'exemple suivant recherche les unités dont le stock est le plus élevé parmi tous les produits.</span><span class="sxs-lookup"><span data-stu-id="e7fdc-108">The following example finds the most units in stock for any product.</span></span>  
  
 <span data-ttu-id="e7fdc-109">Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `125`.</span><span class="sxs-lookup"><span data-stu-id="e7fdc-109">If you run this example against the sample Northwind database, the output is: `125`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="e7fdc-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7fdc-110">Example</span></span>  
 <span data-ttu-id="e7fdc-111">L'exemple suivant utilise Max pour rechercher les `Products` dont le prix unitaire est le plus élevé dans chaque catégorie.</span><span class="sxs-lookup"><span data-stu-id="e7fdc-111">The following example uses Max to find the `Products` that have the highest unit price in each category.</span></span> <span data-ttu-id="e7fdc-112">Les résultats sont ensuite répertoriés par catégorie.</span><span class="sxs-lookup"><span data-stu-id="e7fdc-112">The output then lists the results by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 <span data-ttu-id="e7fdc-113">Si vous exécutez la requête précédente sur l'exemple de base de données Northwind, les résultats se présenteront comme suit :</span><span class="sxs-lookup"><span data-stu-id="e7fdc-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="e7fdc-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7fdc-114">See Also</span></span>  
 [<span data-ttu-id="e7fdc-115">Requêtes d’agrégation</span><span class="sxs-lookup"><span data-stu-id="e7fdc-115">Aggregate Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [<span data-ttu-id="e7fdc-116">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="e7fdc-116">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
