---
title: MessageQueueDuplicatedSocketLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9721a463-15d1-43dc-8e3a-cae44448de91
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 374a5900839dc1f0151743126de16369fa6bf7ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="messagequeueduplicatedsocketleak"></a><span data-ttu-id="83610-102">MessageQueueDuplicatedSocketLeak</span><span class="sxs-lookup"><span data-stu-id="83610-102">MessageQueueDuplicatedSocketLeak</span></span>
<span data-ttu-id="83610-103">ID : 165</span><span class="sxs-lookup"><span data-stu-id="83610-103">Id: 165</span></span>  
  
 <span data-ttu-id="83610-104">Gravité : Erreur</span><span class="sxs-lookup"><span data-stu-id="83610-104">Severity: Error</span></span>  
  
 <span data-ttu-id="83610-105">Catégorie : SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="83610-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="83610-106">Description</span><span class="sxs-lookup"><span data-stu-id="83610-106">Description</span></span>  
 <span data-ttu-id="83610-107">Cet événement indique qu'une erreur s'est produite lors de la répartition d'un socket dupliqué.</span><span class="sxs-lookup"><span data-stu-id="83610-107">This event indicates that an error occurred while dispatching a duplicated socket.</span></span> <span data-ttu-id="83610-108">Ce descripteur est maintenant intégré dans le processus.</span><span class="sxs-lookup"><span data-stu-id="83610-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="83610-109">L'événement répertorie la source, l'exception, le nom de processus et l'ID de processus.</span><span class="sxs-lookup"><span data-stu-id="83610-109">The event lists the Source, Exception, Process Name and Process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83610-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83610-110">See Also</span></span>  
 [<span data-ttu-id="83610-111">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="83610-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="83610-112">Référence générale des événements</span><span class="sxs-lookup"><span data-stu-id="83610-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
