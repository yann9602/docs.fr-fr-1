---
title: "Comment : appeler des fonctions inline définies par l'utilisateur"
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
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b39d71cd0f9aee855133c646fbec6a7f4f6f3c40
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-call-user-defined-functions-inline"></a><span data-ttu-id="276ea-102">Comment : appeler des fonctions inline définies par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="276ea-102">How to: Call User-Defined Functions Inline</span></span>
<span data-ttu-id="276ea-103">Bien que vous puissiez appeler des fonctions inline définies par l'utilisateur, les fonctions incluses dans une requête dont l'exécution est différée ne sont pas exécutées tant que la requête n'est pas exécutée.</span><span class="sxs-lookup"><span data-stu-id="276ea-103">Although you can call user-defined functions inline, functions that are included in a query whose execution is deferred are not executed until the query is executed.</span></span> <span data-ttu-id="276ea-104">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="276ea-104">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="276ea-105">Lorsque vous appelez la même fonction à l'extérieur d'une requête, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée une requête simple à partir de l'expression d'appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="276ea-105">When you call the same function outside a query, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates a simple query from the method call expression.</span></span> <span data-ttu-id="276ea-106">La syntaxe SQL (le paramètre `@p0` est lié à la constante passée) se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="276ea-106">The following is the SQL syntax (the parameter `@p0` is bound to the constant passed in):</span></span>  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="276ea-107"> crée les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="276ea-107"> creates the following:</span></span>  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="276ea-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="276ea-108">Example</span></span>  
 <span data-ttu-id="276ea-109">Dans l’exemple suivant [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requête, vous pouvez consulter un appel inline à la méthode générée fonction définie par l’utilisateur `ReverseCustName`.</span><span class="sxs-lookup"><span data-stu-id="276ea-109">In the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query, you can see an inline call to the generated user-defined function method `ReverseCustName`.</span></span> <span data-ttu-id="276ea-110">La fonction n'est pas exécutée immédiatement, car l'exécution de la requête est différée.</span><span class="sxs-lookup"><span data-stu-id="276ea-110">The function is not executed immediately because query execution is deferred.</span></span> <span data-ttu-id="276ea-111">Le SQL généré pour cette requête se traduit en un appel à la fonction définie par l'utilisateur dans la base de données (consultez le code SQL suivant la requête).</span><span class="sxs-lookup"><span data-stu-id="276ea-111">The SQL built for this query translates to a call to the user-defined function in the database (see the SQL code following the query).</span></span>  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a><span data-ttu-id="276ea-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="276ea-112">See Also</span></span>  
 [<span data-ttu-id="276ea-113">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="276ea-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)
