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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae2b8a8bb536d914edd6c7154136867caee553b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="coordinatorrecoverylogentrycorrupt"></a><span data-ttu-id="2a3bf-102">CoordinatorRecoveryLogEntryCorrupt</span><span class="sxs-lookup"><span data-stu-id="2a3bf-102">CoordinatorRecoveryLogEntryCorrupt</span></span>
<span data-ttu-id="2a3bf-103">ID : 139</span><span class="sxs-lookup"><span data-stu-id="2a3bf-103">Id: 139</span></span>  
  
 <span data-ttu-id="2a3bf-104">Gravité : Erreur</span><span class="sxs-lookup"><span data-stu-id="2a3bf-104">Severity: Error</span></span>  
  
 <span data-ttu-id="2a3bf-105">Catégorie : TransactionBridge</span><span class="sxs-lookup"><span data-stu-id="2a3bf-105">Category: TransactionBridge</span></span>  
  
## <a name="description"></a><span data-ttu-id="2a3bf-106">Description</span><span class="sxs-lookup"><span data-stu-id="2a3bf-106">Description</span></span>  
 <span data-ttu-id="2a3bf-107">Cet événement indique qu'une entrée de journal de récupération de coordinateur a été endommagée et n'a pas pu être désérialisée.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-107">This event indicates that a  coordinator recovery log entry was corrupt and could not be deserialized.</span></span> <span data-ttu-id="2a3bf-108">Cette erreur risque d'entraîner une perte de données.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-108">Data loss may result from this error.</span></span> <span data-ttu-id="2a3bf-109">L’événement répertorie l’ID de transaction, les données de récupération (encodage Base64), l’exception, le nom de processus et l’ID de processus.</span><span class="sxs-lookup"><span data-stu-id="2a3bf-109">The event lists the Transaction ID, Recovery data (Base64 encoded), exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3bf-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a3bf-110">See Also</span></span>  
 [<span data-ttu-id="2a3bf-111">Journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="2a3bf-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="2a3bf-112">Informations de référence générales sur les événements</span><span class="sxs-lookup"><span data-stu-id="2a3bf-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)
