---
title: "Appel de fonctions dans les requêtes LINQ to Entities"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6e50147d356ad9e389a87868205bb9b8b6b3e7b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="34576-102">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="34576-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="34576-103">Les rubriques de cette section expliquent comment appeler des fonctions dans les requêtes LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="34576-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="34576-104">Les classes <xref:System.Data.Objects.EntityFunctions> et <xref:System.Data.Objects.SqlClient.SqlFunctions> donnent accès à des fonctions canoniques et de base de données dans le cadre d'Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="34576-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="34576-105">Pour plus d’informations, consultez [Comment : appeler des fonctions canoniques](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) et [Comment : appeler des fonctions de base de données](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="34576-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="34576-106">L'appel d'une fonction personnalisée passe par trois étapes de base obligatoires :</span><span class="sxs-lookup"><span data-stu-id="34576-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="34576-107">Définissez une fonction dans votre modèle conceptuel ou déclarez-la dans votre modèle de stockage.</span><span class="sxs-lookup"><span data-stu-id="34576-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="34576-108">Ajoutez une méthode à votre application et mappez-la à la fonction du modèle avec un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="34576-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="34576-109">Appelez la fonction dans une requête LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="34576-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="34576-110">Pour plus d'informations, consultez les rubriques de cette section.</span><span class="sxs-lookup"><span data-stu-id="34576-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="34576-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="34576-111">In This Section</span></span>  
 [<span data-ttu-id="34576-112">Comment : appeler des fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="34576-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="34576-113">Comment : appeler des fonctions de base de données</span><span class="sxs-lookup"><span data-stu-id="34576-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="34576-114">Comment : appeler des fonctions de base de données personnalisée</span><span class="sxs-lookup"><span data-stu-id="34576-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="34576-115">Comment : appeler des fonctions définies par le modèle dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="34576-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="34576-116">Comment : appeler des fonctions définies par modèle comme méthodes d’objet</span><span class="sxs-lookup"><span data-stu-id="34576-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="34576-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34576-117">See Also</span></span>  
 [<span data-ttu-id="34576-118">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="34576-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="34576-119">Fonctions canoniques</span><span class="sxs-lookup"><span data-stu-id="34576-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [<span data-ttu-id="34576-120">vue d’ensemble du fichier .edmx</span><span class="sxs-lookup"><span data-stu-id="34576-120">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="34576-121">Comment : définir des fonctions personnalisées dans le modèle conceptuel</span><span class="sxs-lookup"><span data-stu-id="34576-121">How to: Define Custom Functions in the Conceptual Model</span></span>](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)
