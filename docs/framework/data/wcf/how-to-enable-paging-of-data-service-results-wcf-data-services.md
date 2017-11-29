---
title: "Comment : activer la pagination des résultats de services de données (services de données WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6bf267cdc4ab3ec3bdc82a3da52cef21ef1d6b2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="45d22-102">Comment : activer la pagination des résultats de services de données (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="45d22-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="45d22-103"> vous permet de limiter le nombre d'entités retourné par une requête de service des données.</span><span class="sxs-lookup"><span data-stu-id="45d22-103"> enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="45d22-104">Les limites de page sont définies dans la méthode appelée lorsque le service est initialisé et peuvent être définies séparément pour chaque jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="45d22-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="45d22-105">Lorsque la pagination est activée, la dernière entrée dans le flux contient un lien vers la page suivante de données.</span><span class="sxs-lookup"><span data-stu-id="45d22-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="45d22-106">Pour plus d’informations, consultez [configuration du Service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="45d22-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="45d22-107">Cette rubrique indique comment modifier un service de données pour permettre la pagination de `Customers` retournés et de jeux d'entités `Orders`.</span><span class="sxs-lookup"><span data-stu-id="45d22-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="45d22-108">L'exemple de cette rubrique utilise l'exemple du service de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="45d22-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="45d22-109">Ce service est créé lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="45d22-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="45d22-110">Comment permettre la pagination de clients retournés et de jeux d'entités de commandes</span><span class="sxs-lookup"><span data-stu-id="45d22-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="45d22-111">Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="45d22-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="45d22-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45d22-112">See Also</span></span>  
 [<span data-ttu-id="45d22-113">Chargement de contenu différé</span><span class="sxs-lookup"><span data-stu-id="45d22-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [<span data-ttu-id="45d22-114">Comment : charger des résultats paginés</span><span class="sxs-lookup"><span data-stu-id="45d22-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
