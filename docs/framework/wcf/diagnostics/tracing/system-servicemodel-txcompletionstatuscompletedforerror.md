---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bce99f11ba5a18e80c24fc51e65b66de97f9e7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="4cf75-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="4cf75-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="4cf75-103">La transaction spécifiée pour l’opération spécifiée a été effectuée en raison d’une exception d’exécution non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="4cf75-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4cf75-104">Description</span><span class="sxs-lookup"><span data-stu-id="4cf75-104">Description</span></span>  
 <span data-ttu-id="4cf75-105">Suivi lorsqu'une erreur se produit durant une tentative d'exécution de la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="4cf75-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="4cf75-106">Cela se produit avant qu'une réponse ou une erreur ne soit envoyée à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="4cf75-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4cf75-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="4cf75-107">Troubleshooting</span></span>  
 <span data-ttu-id="4cf75-108">Inspectez le message tracé pour le message d'exception et tout élément sur lequel une action peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="4cf75-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf75-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cf75-109">See Also</span></span>  
 [<span data-ttu-id="4cf75-110">Le suivi</span><span class="sxs-lookup"><span data-stu-id="4cf75-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4cf75-111">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="4cf75-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4cf75-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="4cf75-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
