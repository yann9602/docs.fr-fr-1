---
title: "Intercepteurs (services de données WCF)"
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
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7aad516b819723c97a40a016a46ddcbe0fcdf4d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="821b1-102">Intercepteurs (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="821b1-102">Interceptors (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="821b1-103">permet à une application intercepter les messages de demande afin que vous pouvez ajouter une logique personnalisée à une opération.</span><span class="sxs-lookup"><span data-stu-id="821b1-103"> enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="821b1-104">Vous pouvez utiliser cette logique personnalisée pour valider les données dans les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="821b1-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="821b1-105">Vous pouvez également l'utiliser pour restreindre davantage l'étendue d'une requête d'interrogation, comme l'insertion d'une stratégie d'autorisation personnalisée sur la base de chaque demande.</span><span class="sxs-lookup"><span data-stu-id="821b1-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="821b1-106">L'interception est effectuée par les méthodes attribuées spécialement dans le service de données.</span><span class="sxs-lookup"><span data-stu-id="821b1-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="821b1-107">Ces méthodes sont appelées par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] au point approprié dans le traitement du message.</span><span class="sxs-lookup"><span data-stu-id="821b1-107">These methods are called by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] at the appropriate point in message processing.</span></span> <span data-ttu-id="821b1-108">Les intercepteurs sont définis sur une base de jeu par entité et les méthodes d’intercepteur ne peut pas accepter de paramètres à partir de la requête telles que les opérations de service peuvent.</span><span class="sxs-lookup"><span data-stu-id="821b1-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="821b1-109">Les méthodes d’intercepteur de requête, appelées lors du traitement d’une requête HTTP GET, doivent retourner une expression lambda qui détermine si une instance d’entité de l’intercepteur doit être retournée par les résultats de requête.</span><span class="sxs-lookup"><span data-stu-id="821b1-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="821b1-110">Cette expression est utilisée par le service de données pour affiner davantage l'opération demandée.</span><span class="sxs-lookup"><span data-stu-id="821b1-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="821b1-111">L'exemple suivant illustre la définition d'un intercepteur de requête.</span><span class="sxs-lookup"><span data-stu-id="821b1-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="821b1-112">Pour plus d’informations, consultez [Comment : intercepter des Messages de Service de données](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="821b1-112">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="821b1-113">Les intercepteurs de modification, appelés lors du traitement d'opérations de non-requête, doivent retourner `void` (`Nothing` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="821b1-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="821b1-114">Les méthodes d'intercepteur de requête doivent accepter les deux paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="821b1-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1.  <span data-ttu-id="821b1-115">Un paramètre d'un type qui est compatible avec le type d'entité du jeu d'entités.</span><span class="sxs-lookup"><span data-stu-id="821b1-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="821b1-116">Lorsque le service de données appelle l'intercepteur de modification, la valeur de ce paramètre reflétera les informations d'entité envoyées par la demande.</span><span class="sxs-lookup"><span data-stu-id="821b1-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2.  <span data-ttu-id="821b1-117">Un paramètre de type <xref:System.Data.Services.UpdateOperations>.</span><span class="sxs-lookup"><span data-stu-id="821b1-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="821b1-118">Lorsque le service de données appelle l'intercepteur de modification, la valeur de ce paramètre reflétera l'opération que tente d'effectuer la demande.</span><span class="sxs-lookup"><span data-stu-id="821b1-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="821b1-119">L'exemple suivant illustre la définition d'un intercepteur de modification.</span><span class="sxs-lookup"><span data-stu-id="821b1-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="821b1-120">Pour plus d’informations, consultez [Comment : intercepter des Messages de Service de données](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="821b1-120">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="821b1-121">Les attributs suivants sont pris en charge pour l'interception.</span><span class="sxs-lookup"><span data-stu-id="821b1-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="821b1-122">**[QueryInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="821b1-122">**[QueryInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="821b1-123">Les méthodes qui appliquent l'attribut <xref:System.Data.Services.QueryInterceptorAttribute> sont appelées lorsqu'une demande HTTP GET est reçue pour la ressource de jeu d'entités ciblée.</span><span class="sxs-lookup"><span data-stu-id="821b1-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="821b1-124">Ces méthodes doivent toujours retourner une expression lambda sous la forme `Expression<Func<T,bool>>`.</span><span class="sxs-lookup"><span data-stu-id="821b1-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="821b1-125">**[ChangeInterceptor (** *EnitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="821b1-125">**[ChangeInterceptor(** *EnitySetName* **)]**</span></span>  
 <span data-ttu-id="821b1-126">Les méthodes qui appliquent l'attribut <xref:System.Data.Services.ChangeInterceptorAttribute> sont appelées lorsqu'une demande HTTP différente d'une demande HTTP GET est reçue pour la ressource de jeu d'entités ciblée.</span><span class="sxs-lookup"><span data-stu-id="821b1-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="821b1-127">Ces méthodes doivent toujours retourner `void` (`Nothing` en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="821b1-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="821b1-128">Pour plus d’informations, consultez [Comment : intercepter des Messages de Service de données](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="821b1-128">For more information, see [How to: Intercept Data Service Messages](../../../../docs/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821b1-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="821b1-129">See Also</span></span>  
 [<span data-ttu-id="821b1-130">Opérations de service</span><span class="sxs-lookup"><span data-stu-id="821b1-130">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)
