---
title: "Procédure : activer l'accès au service de données (WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b41de296143d325ba0e1932831d4a3ef1bd7dc80
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="1f9a3-102">Procédure : activer l'accès au service de données (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="1f9a3-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="1f9a3-103">Dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous devez accorder explicitement l'accès aux ressources exposées par un service de données.</span><span class="sxs-lookup"><span data-stu-id="1f9a3-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="1f9a3-104">Cela signifie qu'après avoir créé un service de données, vous devez encore fournir explicitement l'accès à des ressources individuelles comme les jeux d'entités.</span><span class="sxs-lookup"><span data-stu-id="1f9a3-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="1f9a3-105">Cette rubrique montre comment activer la lecture et écriture aux cinq de l’entité définit dans le service de données Northwind est créé lorsque vous complétez le [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1f9a3-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="1f9a3-106">Puisque l'énumération <xref:System.Data.Services.EntitySetRights> est définie à l'aide de l'objet <xref:System.FlagsAttribute>, vous pouvez utiliser un opérateur OR logique pour spécifier plusieurs autorisations pour un jeu d'entités unique.</span><span class="sxs-lookup"><span data-stu-id="1f9a3-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f9a3-107">Tout client qui peut accéder à l'application ASP.NET peut également accéder aux ressources exposées par le service de données.</span><span class="sxs-lookup"><span data-stu-id="1f9a3-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="1f9a3-108">Dans un service de données de production, pour empêcher l'accès non autorisé aux ressources, vous devez également sécuriser l'application elle-même.</span><span class="sxs-lookup"><span data-stu-id="1f9a3-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="1f9a3-109">Pour plus d’informations, consultez [NIB : sécurité ASP.NET](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="1f9a3-109">For more information, see [NIB: ASP.NET Security](http://msdn.microsoft.com/en-us/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="1f9a3-110">Pour activer l'accès au service de données</span><span class="sxs-lookup"><span data-stu-id="1f9a3-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="1f9a3-111">Dans le code du service de données, remplacez le code d'espace réservé dans la fonction `InitializeService` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="1f9a3-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="1f9a3-112">Cela permet aux clients de disposer d'un accès en lecture et en écriture aux jeux d'entités `Orders` et `Order_Details` et d'un accès en lecture seule aux jeux d'entités `Customers`.</span><span class="sxs-lookup"><span data-stu-id="1f9a3-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9a3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f9a3-113">See Also</span></span>  
 [<span data-ttu-id="1f9a3-114">Comment : développer un Service de données WCF en cours d’exécution sur IIS</span><span class="sxs-lookup"><span data-stu-id="1f9a3-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="1f9a3-115">Configuration du Service de données</span><span class="sxs-lookup"><span data-stu-id="1f9a3-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
