---
title: Interrogation de relations
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
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 03c2da9f65964a9ed43d1e82abf779b43be733ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="querying-across-relationships"></a><span data-ttu-id="70503-102">Interrogation de relations</span><span class="sxs-lookup"><span data-stu-id="70503-102">Querying Across Relationships</span></span>
<span data-ttu-id="70503-103">Les références à d’autres objets ou collections d’autres objets dans vos définitions de classe correspondent directement à des relations de clé étrangère dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="70503-103">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="70503-104">Vous pouvez utiliser ces relations lorsque vous effectuez une interrogation avec la notation par point pour accéder aux propriétés de relation et naviguer entre les objets.</span><span class="sxs-lookup"><span data-stu-id="70503-104">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="70503-105">Ces opérations d'accès sont traduites en jointures complexes ou en sous-requêtes corrélées plus complexes dans le SQL équivalent.</span><span class="sxs-lookup"><span data-stu-id="70503-105">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="70503-106">Par exemple, la requête suivante navigue des commandes aux clients afin de limiter les résultats aux commandes des clients localisés à Londres.</span><span class="sxs-lookup"><span data-stu-id="70503-106">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="70503-107">Si les propriétés de la relation n’existent pas, vous devez les écrire manuellement en tant que *jointures*, tout comme vous le feriez dans une requête SQL, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="70503-107">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="70503-108">Vous pouvez utiliser la *relation* propriété à définir cette relation spécifique à une seule fois.</span><span class="sxs-lookup"><span data-stu-id="70503-108">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="70503-109">Vous pouvez ensuite utiliser la syntaxe à point qui est plus pratique.</span><span class="sxs-lookup"><span data-stu-id="70503-109">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="70503-110">Toutefois, les propriétés de relation sont plus importantes en raison du fait que les modèles objet spécifiques au domaine sont généralement définis comme des hiérarchies ou des graphiques.</span><span class="sxs-lookup"><span data-stu-id="70503-110">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="70503-111">Les objets par rapport auxquels vous effectuez la programmation ont des références à d'autres objets.</span><span class="sxs-lookup"><span data-stu-id="70503-111">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="70503-112">C'est une simple coïncidence que les relations entre objets correspondent aux relations de clé étrangère dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="70503-112">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="70503-113">L'accès aux propriétés permet ensuite d'écrire facilement des jointures.</span><span class="sxs-lookup"><span data-stu-id="70503-113">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="70503-114">À cet égard, les propriétés de relation sont plus importantes du point de vue des résultats d'une requête que de la requête elle-même.</span><span class="sxs-lookup"><span data-stu-id="70503-114">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="70503-115">Une fois que la requête a récupéré des données concernant un client spécifique, la définition de classe indique que les clients ont des commandes.</span><span class="sxs-lookup"><span data-stu-id="70503-115">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="70503-116">En d'autres termes, la propriété `Orders` d'un client spécifique doit être une collection comportant toutes les commandes de ce client.</span><span class="sxs-lookup"><span data-stu-id="70503-116">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="70503-117">Il s'agit en fait du contrat que vous avez déclaré en définissant les classes de cette manière.</span><span class="sxs-lookup"><span data-stu-id="70503-117">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="70503-118">Vous vous attendez à voir apparaître les commandes même si la requête ne les a pas demandées.</span><span class="sxs-lookup"><span data-stu-id="70503-118">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="70503-119">Vous souhaitez que votre modèle objet continue de donner l'impression qu'il s'agit d'une extension en mémoire de la base de données avec les objets connexes immédiatement disponibles.</span><span class="sxs-lookup"><span data-stu-id="70503-119">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="70503-120">Maintenant que vous disposez de relations, vous pouvez écrire des requêtes en faisant référence aux propriétés de relation définies dans vos classes.</span><span class="sxs-lookup"><span data-stu-id="70503-120">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="70503-121">Ces références de relation correspondent aux relations de clé étrangère dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="70503-121">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="70503-122">Les opérations qui utilisent ces relations sont traduites en jointures plus complexes dans le SQL équivalent.</span><span class="sxs-lookup"><span data-stu-id="70503-122">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="70503-123">À partir du moment où vous avez défini une relation (à l'aide de l'attribut <xref:System.Data.Linq.Mapping.AssociationAttribute>), il n'est pas nécessaire de coder une jointure explicite dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70503-123">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="70503-124">Pour aider à maintenir cette impression, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implémente une technique appelée *chargement différé*.</span><span class="sxs-lookup"><span data-stu-id="70503-124">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="70503-125">Pour plus d’informations, consultez [différée / chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="70503-125">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="70503-126">Considérez la requête SQL suivante pour projeter une liste de `CustomerID` - `OrderID` paires :</span><span class="sxs-lookup"><span data-stu-id="70503-126">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```  
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="70503-127">Pour obtenir les mêmes résultats avec [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous utilisez la référence de propriété `Orders` qui existe déjà dans la classe `Customer`.</span><span class="sxs-lookup"><span data-stu-id="70503-127">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="70503-128">Le `Orders` référence fournit les informations nécessaires pour exécuter la requête et projeter le `CustomerID` - `OrderID` paires, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="70503-128">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="70503-129">Vous pouvez également effectuer l'opération inverse.</span><span class="sxs-lookup"><span data-stu-id="70503-129">You can also do the reverse.</span></span> <span data-ttu-id="70503-130">Vous pouvez en effet interroger `Orders` et utiliser sa référence de relation `Customer` pour accéder aux informations sur l'objet `Customer` associé.</span><span class="sxs-lookup"><span data-stu-id="70503-130">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="70503-131">Le code suivant projette la même `CustomerID` - `OrderID` paires comme avant, mais cette fois en interrogeant `Orders` au lieu de `Customers`.</span><span class="sxs-lookup"><span data-stu-id="70503-131">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="70503-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70503-132">See Also</span></span>  
 [<span data-ttu-id="70503-133">Concepts relatifs aux requêtes</span><span class="sxs-lookup"><span data-stu-id="70503-133">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
