---
title: "Service : appels ayant renvoyé une erreur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: daae4da05e2c1d68147f23256d868a6124479417
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="service-calls-faulted"></a><span data-ttu-id="aa783-102">Service : appels ayant renvoyé une erreur</span><span class="sxs-lookup"><span data-stu-id="aa783-102">Service: Calls Faulted</span></span>
<span data-ttu-id="aa783-103">Nom du compteur : appels ayant renvoyé des erreurs.</span><span class="sxs-lookup"><span data-stu-id="aa783-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="aa783-104">Description</span><span class="sxs-lookup"><span data-stu-id="aa783-104">Description</span></span>  
 <span data-ttu-id="aa783-105">Nombre d'appels effectués vers ce service ayant retourné une erreur.</span><span class="sxs-lookup"><span data-stu-id="aa783-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="aa783-106">Dans les applications [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], les méthodes de service communiquent des informations sur l'erreur de traitement à l'aide de messages d'erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="aa783-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="aa783-107">Les erreurs SOAP sont des types de message inclus dans les métadonnées d'une opération de service et créent, par conséquent, un contrat d'erreur permettant aux clients d'améliorer la fiabilité ou l'interactivité de leur exécution.</span><span class="sxs-lookup"><span data-stu-id="aa783-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="aa783-108">Les erreurs SOAP étant exprimées aux clients dans un format XML, elles sont très interopérables.</span><span class="sxs-lookup"><span data-stu-id="aa783-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa783-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa783-109">See Also</span></span>  
 [<span data-ttu-id="aa783-110">Spécification et gestion des erreurs dans les contrats et les services</span><span class="sxs-lookup"><span data-stu-id="aa783-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
