---
title: "Personnalisation d'opérations à l'aide de procédures stockées uniquement"
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
ms.assetid: 441e8ef3-998c-4d12-8825-ce66a178f90f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: eba9e4462c1a71708173994dfb3efaf4199248c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-by-using-stored-procedures-exclusively"></a><span data-ttu-id="b0ccd-102">Personnalisation d'opérations à l'aide de procédures stockées uniquement</span><span class="sxs-lookup"><span data-stu-id="b0ccd-102">Customizing Operations by Using Stored Procedures Exclusively</span></span>
<span data-ttu-id="b0ccd-103">L'accès aux données se fait couramment à l'aide de procédures stockées uniquement.</span><span class="sxs-lookup"><span data-stu-id="b0ccd-103">Access to data by using only stored procedures is a common scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0ccd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b0ccd-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b0ccd-105">Description</span><span class="sxs-lookup"><span data-stu-id="b0ccd-105">Description</span></span>  
 <span data-ttu-id="b0ccd-106">Vous pouvez modifier l’exemple fourni dans [personnalisation des opérations par à l’aide de procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) en remplaçant les même la première requête (ce qui implique l’exécution de SQL dynamique) par un appel de méthode qui encapsule une procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="b0ccd-106">You can modify the example provided in [Customizing Operations By Using Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md) by replacing even the first query (which causes dynamic SQL execution) with a method call that wraps a stored procedure.</span></span>  
  
 <span data-ttu-id="b0ccd-107">Supposons que `CustomersByCity` est la méthode, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b0ccd-107">Assume `CustomersByCity` is the method, as in the following example.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b0ccd-108">Code</span><span class="sxs-lookup"><span data-stu-id="b0ccd-108">Code</span></span>  
 [!code-csharp[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#4)]
 [!code-vb[DLinqOverrideDefaultSproc#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#4)]  
  
 <span data-ttu-id="b0ccd-109">Le code suivant s'exécute sans SQL dynamique.</span><span class="sxs-lookup"><span data-stu-id="b0ccd-109">The following code executes without any dynamic SQL.</span></span>  
  
 [!code-csharp[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#5)]
 [!code-vb[DLinqOverrideDefaultSproc#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b0ccd-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0ccd-110">See Also</span></span>  
 [<span data-ttu-id="b0ccd-111">Responsabilités du développeur en matière de substitution du comportement par défaut</span><span class="sxs-lookup"><span data-stu-id="b0ccd-111">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
