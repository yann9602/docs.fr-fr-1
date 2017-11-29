---
title: USING (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c506484908d6b0ffe3a11e33b51d0bcc2d27c25c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-entity-sql"></a><span data-ttu-id="27fe6-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="27fe6-102">USING (Entity SQL)</span></span>
<span data-ttu-id="27fe6-103">Spécifie les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="27fe6-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fe6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27fe6-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="27fe6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="27fe6-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="27fe6-106">Spécifie un alias plus court avec lequel qualifier un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="27fe6-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="27fe6-107">Tout espace de noms valide.</span><span class="sxs-lookup"><span data-stu-id="27fe6-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27fe6-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="27fe6-108">Example</span></span>  
 <span data-ttu-id="27fe6-109">La requête Entity SQL ci-dessous utilise l'opérateur USING pour spécifier les espaces de noms utilisés dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="27fe6-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="27fe6-110">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="27fe6-110">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="27fe6-111">Suivez la procédure de [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="27fe6-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="27fe6-112">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="27fe6-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="27fe6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27fe6-113">See Also</span></span>  
 [<span data-ttu-id="27fe6-114">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="27fe6-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [<span data-ttu-id="27fe6-115">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="27fe6-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
