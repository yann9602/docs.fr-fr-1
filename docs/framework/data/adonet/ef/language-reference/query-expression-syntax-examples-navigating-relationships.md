---
title: "Exemples de syntaxe d'expression de requête : parcours des relations"
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
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 85e023eb07d247a032453d15b53ce94a89991806
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="9c067-102">Exemples de syntaxe d'expression de requête : parcours des relations</span><span class="sxs-lookup"><span data-stu-id="9c067-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="9c067-103">Les propriétés de navigation dans [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] sont des propriétés de raccourci utilisées pour rechercher les entités situées aux terminaisons d'une association.</span><span class="sxs-lookup"><span data-stu-id="9c067-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="9c067-104">Les propriétés de navigation permettent à un utilisateur de naviguer d'une entité à une autre ou d'une entité à des entités associées par le biais d'un ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="9c067-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="9c067-105">Cette rubrique fournit des exemples dans une syntaxe d'expression de requête sur la façon d'explorer des relations au moyen de propriétés de navigation dans des requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c067-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="9c067-106">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9c067-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9c067-107">Les exemples de cette rubrique utilisent les éléments suivants `using` / `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="9c067-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="9c067-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c067-108">Example</span></span>  
 <span data-ttu-id="9c067-109">L'exemple ci-dessous utilise la méthode <xref:System.Linq.Queryable.Select%2A> pour obtenir tous les ID de contact et la somme du montant total dû pour chaque contact dont le nom est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="9c067-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="9c067-110">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="9c067-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="9c067-111">La méthode `Sum` utilise la propriété de navigation `Contact.SalesOrderHeader` pour calculer la somme du montant total dû pour l'ensemble des commandes de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="9c067-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="9c067-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c067-112">Example</span></span>  
 <span data-ttu-id="9c067-113">L'exemple ci-dessous obtient toutes les commandes des contacts dont le nom est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="9c067-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="9c067-114">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="9c067-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="9c067-115">Le nom et les commandes du contact sont retournés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="9c067-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="9c067-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c067-116">Example</span></span>  
 <span data-ttu-id="9c067-117">L'exemple ci-dessous utilise les propriétés de navigation `SalesOrderHeader.Address` et `SalesOrderHeader.Contact` pour obtenir la collection des objets `Address` et `Contact` associés à chaque commande.</span><span class="sxs-lookup"><span data-stu-id="9c067-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="9c067-118">Le nom du contact, l'adresse, le numéro de commande et le montant total dû de chaque commande pour la ville de Seattle sont retournés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="9c067-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="9c067-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="9c067-119">Example</span></span>  
 <span data-ttu-id="9c067-120">L'exemple ci-dessous utilise la méthode `Where` pour rechercher des commandes qui ont été passées après le 1er décembre 2003, puis utilise la propriété de navigation `order.SalesOrderDetail` pour obtenir les détails de chaque commande.</span><span class="sxs-lookup"><span data-stu-id="9c067-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="9c067-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c067-121">See Also</span></span>  
 [<span data-ttu-id="9c067-122">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9c067-122">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
