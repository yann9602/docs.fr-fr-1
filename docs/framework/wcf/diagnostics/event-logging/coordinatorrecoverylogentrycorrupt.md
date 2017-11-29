---
title: CoordinatorRecoveryLogEntryCorrupt
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cd0c3e3-84c8-4d43-a561-a8851c78e565
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1db6f8dc4136623f35767c122dbea46fd4706b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="a0017-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="a0017-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="a0017-103">ID : 139</span><span class="sxs-lookup"><span data-stu-id="a0017-103">Id: 139</span></span>  
  
 <span data-ttu-id="a0017-104">Gravité : Erreur</span><span class="sxs-lookup"><span data-stu-id="a0017-104">Severity: Error</span></span>  
  
 <span data-ttu-id="a0017-105">Catégorie : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="a0017-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="a0017-106">Description</span><span class="sxs-lookup"><span data-stu-id="a0017-106">Description</span></span>  
 <span data-ttu-id="a0017-107">Cet événement indique qu'une entrée de journal de récupération de coordinateur a été endommagée et n'a pas pu être désérialisée.</span><span class="sxs-lookup"><span data-stu-id="a0017-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="a0017-108">Cette erreur risque d'entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="a0017-108">Data loss may result from this error.</span></span> <span data-ttu-id="a0017-109">L’événement répertorie l’ID de transaction, les données de récupération (encodage Base64), l’exception, le nom de processus et l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="a0017-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0017-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0017-110">See Also</span></span>  
 [<span data-ttu-id="a0017-111">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="a0017-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="a0017-112">Référence générale des événements</span><span class="sxs-lookup"><span data-stu-id="a0017-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
