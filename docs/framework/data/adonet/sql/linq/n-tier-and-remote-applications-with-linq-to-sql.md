---
title: Applications multicouches et distantes avec LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 004e64584027d40368592097c76ad0830e942f07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="055e9-102">Applications multicouches et distantes avec LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="055e9-102">N-Tier and Remote Applications with LINQ to SQL</span></span>
<span data-ttu-id="055e9-103">Vous pouvez créer des applications multicouches qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="055e9-103">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="055e9-104">En règle générale, le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] contexte de données, les classes d’entité et la logique de construction de requête se trouvent sur la couche intermédiaire en tant que la couche d’accès aux données (DAL).</span><span class="sxs-lookup"><span data-stu-id="055e9-104">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="055e9-105">La logique métier et toutes les données non persistantes peuvent être implémentées entièrement dans des classes et des méthodes partielles et le contexte de données, ou ils peuvent être implémentés dans des classes distinctes.</span><span class="sxs-lookup"><span data-stu-id="055e9-105">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>  
  
 <span data-ttu-id="055e9-106">Le niveau client ou la couche Présentation appelle des méthodes sur l'interface distante de la couche intermédiaire, et la couche Data Access sur cette couche exécutera des requêtes ou des procédures stockées qui sont mappées aux méthodes <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="055e9-106">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="055e9-107">La couche intermédiaire retourne les données aux clients généralement sous la forme de représentations XML d'entités ou objets proxy.</span><span class="sxs-lookup"><span data-stu-id="055e9-107">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>  
  
 <span data-ttu-id="055e9-108">Sur la couche intermédiaire, les entités sont créées par le contexte de données, qui suit leur état et gère le chargement et la soumission différés des modifications à partir de et vers la base de données.</span><span class="sxs-lookup"><span data-stu-id="055e9-108">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="055e9-109">Ces entités sont "attachées" au `DataContext`.</span><span class="sxs-lookup"><span data-stu-id="055e9-109">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="055e9-110">Toutefois, après que les entités ont été envoyées vers une autre couche par le biais de la sérialisation, elles deviennent détachées, ce qui signifie que `DataContext` ne suit plus leur état.</span><span class="sxs-lookup"><span data-stu-id="055e9-110">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="055e9-111">Les entités que le client renvoie pour les mises à jour doivent être préalablement rattachées au contexte de données pour que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] puisse soumettre les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="055e9-111">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="055e9-112">Le client est chargé de renvoyer les valeurs et/ou horodatages d'origine à la couche intermédiaire si ceux-ci sont requis pour les contrôles d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="055e9-112">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>  
  
 <span data-ttu-id="055e9-113">Dans les applications ASP.NET, <xref:System.Web.UI.WebControls.LinqDataSource> gère la plus grande part de cette complexité.</span><span class="sxs-lookup"><span data-stu-id="055e9-113">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="055e9-114">Pour plus d’informations, consultez [NIB : vue d’ensemble du contrôle serveur Web LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="055e9-114">For more information, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="055e9-115">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="055e9-115">Additional Resources</span></span>  
 <span data-ttu-id="055e9-116">Pour plus d'informations sur l'implémentation des applications multicouches qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="055e9-116">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>  
  
-   [<span data-ttu-id="055e9-117">Applications multicouches LINQ to SQL avec ASP.NET</span><span class="sxs-lookup"><span data-stu-id="055e9-117">LINQ to SQL N-Tier with ASP.NET</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [<span data-ttu-id="055e9-118">Applications multicouches LINQ to SQL avec les services web</span><span class="sxs-lookup"><span data-stu-id="055e9-118">LINQ to SQL N-Tier with Web Services</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [<span data-ttu-id="055e9-119">LINQ to SQL avec des applications client-serveur fortement couplées</span><span class="sxs-lookup"><span data-stu-id="055e9-119">LINQ to SQL with Tightly-Coupled Client-Server Applications</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [<span data-ttu-id="055e9-120">Implémentation de la logique métier dans les applications multicouches</span><span class="sxs-lookup"><span data-stu-id="055e9-120">Implementing N-Tier Business Logic</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [<span data-ttu-id="055e9-121">Récupération de données et opérations CUD dans les applications multicouches (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="055e9-121">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 <span data-ttu-id="055e9-122">Pour plus d’informations sur les applications multicouches qui utilisent des groupes de données ADO.NET, consultez [travailler avec les jeux de données dans les applications multicouches](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span><span class="sxs-lookup"><span data-stu-id="055e9-122">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055e9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="055e9-123">See Also</span></span>  
 [<span data-ttu-id="055e9-124">Informations générales</span><span class="sxs-lookup"><span data-stu-id="055e9-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
