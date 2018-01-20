---
title: "Exemples de syntaxe de requête basée sur une méthode : parcours des relations"
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
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 42ea8030a9d832117a10feb6b937d05807033c91
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="440d9-102">Exemples de syntaxe de requête basée sur une méthode : parcours des relations</span><span class="sxs-lookup"><span data-stu-id="440d9-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="440d9-103">Les propriétés de navigation dans [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] sont des propriétés de raccourci utilisées pour rechercher les entités situées aux terminaisons d'une association.</span><span class="sxs-lookup"><span data-stu-id="440d9-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="440d9-104">Les propriétés de navigation permettent à un utilisateur de naviguer d'une entité à une autre ou d'une entité à des entités associées par le biais d'un ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="440d9-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="440d9-105">Cette rubrique fournit des exemples de syntaxe de requête fondée sur une méthode relatifs à la façon d'explorer des relations au moyen de propriétés de navigation dans des requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="440d9-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="440d9-106">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="440d9-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="440d9-107">Les exemples de cette rubrique utilisent les éléments suivants `using` / `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="440d9-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="440d9-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="440d9-108">Example</span></span>  
 <span data-ttu-id="440d9-109">L'exemple suivant de syntaxe de requête fondée sur une méthode utilise la méthode <xref:System.Linq.Queryable.SelectMany%2A> pour obtenir toutes les commandes des contacts dont le nom de famille est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="440d9-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="440d9-110">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="440d9-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="440d9-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="440d9-111">Example</span></span>  
 <span data-ttu-id="440d9-112">L'exemple suivant de syntaxe de requête fondée sur une méthode utilise la méthode <xref:System.Linq.Queryable.Select%2A> pour obtenir tous les ID de contact et la somme du montant total dû pour chaque contact dont le nom est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="440d9-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="440d9-113">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="440d9-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="440d9-114">La méthode `Sum` utilise la propriété de navigation `Contact.SalesOrderHeader` pour calculer la somme du montant total dû pour l'ensemble des commandes de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="440d9-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="440d9-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="440d9-115">Example</span></span>  
 <span data-ttu-id="440d9-116">L'exemple suivant de syntaxe de requête fondée sur une méthode obtient toutes les commandes des contacts dont le nom de famille est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="440d9-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="440d9-117">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="440d9-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="440d9-118">Le nom et les commandes du contact sont retournés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="440d9-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="440d9-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="440d9-119">Example</span></span>  
 <span data-ttu-id="440d9-120">L'exemple ci-dessous utilise les propriétés de navigation `SalesOrderHeader.Address` et `SalesOrderHeader.Contact` pour obtenir la collection des objets `Address` et `Contact` associés à chaque commande.</span><span class="sxs-lookup"><span data-stu-id="440d9-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="440d9-121">Le nom du contact, l'adresse, le numéro de commande et le montant total dû de chaque commande pour la ville de Seattle sont retournés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="440d9-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="440d9-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="440d9-122">Example</span></span>  
 <span data-ttu-id="440d9-123">L'exemple ci-dessous utilise la méthode `Where` pour rechercher des commandes qui ont été passées après le 1er décembre 2003, puis utilise la propriété de navigation `order.SalesOrderDetail` pour obtenir les détails de chaque commande.</span><span class="sxs-lookup"><span data-stu-id="440d9-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="440d9-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="440d9-124">See Also</span></span>  
 [<span data-ttu-id="440d9-125">Propriétés de navigation</span><span class="sxs-lookup"><span data-stu-id="440d9-125">Navigation Properties</span></span>](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [<span data-ttu-id="440d9-126">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="440d9-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
