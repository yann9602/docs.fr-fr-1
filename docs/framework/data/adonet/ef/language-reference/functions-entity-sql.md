---
title: Fonctions (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb55fecc7c876fda5918418e353eaf327ce6c034
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="functions-entity-sql"></a><span data-ttu-id="44089-102">Fonctions (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="44089-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="44089-103">Entity SQL prend en charge les fonctions définies par l'utilisateur, les fonctions canoniques et les fonctions spécifiques au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="44089-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="44089-104">Les fonctions définies par l'utilisateur sont spécifiées dans le modèle conceptuel ou inline dans la requête.</span><span class="sxs-lookup"><span data-stu-id="44089-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="44089-105">Pour plus d’informations, consultez [les fonctions définies par l’utilisateur](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="44089-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="44089-106">Les fonctions canoniques sont prédéfinies dans Entity Framework et doivent être prises en charge par les fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="44089-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="44089-107">Les commandes Entity SQL échouent si un utilisateur appelle une fonction qui n'est pas prise en charge par un fournisseur.</span><span class="sxs-lookup"><span data-stu-id="44089-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="44089-108">Par conséquent, les fonctions canoniques sont généralement recommandées par rapport aux fonctions spécifiques au magasin, qui se trouvent dans un espace de noms spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="44089-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="44089-109">Pour plus d’informations, consultez [fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="44089-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="44089-110">Le fournisseur managé Client Microsoft SQL fournit un jeu de fonctions spécifiques au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="44089-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="44089-111">Pour plus d’informations, consultez [fonctions SqlClient pour Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="44089-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="44089-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="44089-112">In This Section</span></span>  
 [<span data-ttu-id="44089-113">Fonctions définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="44089-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="44089-114">Résolution de surcharge de fonction</span><span class="sxs-lookup"><span data-stu-id="44089-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="44089-115">Fonctions d’agrégation</span><span class="sxs-lookup"><span data-stu-id="44089-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="44089-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44089-116">See Also</span></span>  
 [<span data-ttu-id="44089-117">Vue d’ensemble de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="44089-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
