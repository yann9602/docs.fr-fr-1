---
title: "+ (Concaténation de chaînes) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6019f6025b3a3996c9b86a6c9e61a3dd345c1b12
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="d8d51-102">+ (concaténation de chaînes) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d8d51-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="d8d51-103">Concatène deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="d8d51-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8d51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8d51-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8d51-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d8d51-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d8d51-106">Toute expression valide de l'un des types de données EDM.String.</span><span class="sxs-lookup"><span data-stu-id="d8d51-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="d8d51-107">Les deux expressions doivent être du même type de données. Si tel n'est pas le cas, l'une doit être implicitement convertible dans le type de données de l'autre.</span><span class="sxs-lookup"><span data-stu-id="d8d51-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d8d51-108">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="d8d51-108">Result Types</span></span>  
 <span data-ttu-id="d8d51-109">Type de données qui résulte de la promotion de type implicite de deux arguments.</span><span class="sxs-lookup"><span data-stu-id="d8d51-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d8d51-110">Pour plus d’informations sur la promotion de type implicite, consultez [système de Type](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d8d51-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8d51-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8d51-111">Example</span></span>  
 <span data-ttu-id="d8d51-112">La requête Entity SQL ci-dessous utilise l'opérateur + pour concaténer deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="d8d51-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="d8d51-113">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="d8d51-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d8d51-114">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d8d51-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d8d51-115">Suivez la procédure de [Comment : exécuter une requête qui retourne des résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d8d51-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="d8d51-116">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="d8d51-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="d8d51-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8d51-117">See Also</span></span>  
 [<span data-ttu-id="d8d51-118">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d8d51-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d8d51-119">Types de modèle conceptuel (CSDL)</span><span class="sxs-lookup"><span data-stu-id="d8d51-119">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4)
