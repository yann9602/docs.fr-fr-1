---
title: System.ServiceModel.Activation.WebHostServiceCloseFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3cab9856-a5cf-4f0e-a0cb-89425e368f8e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2b0dc75e8e8748e25c1faf28150e0c156a20ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelactivationwebhostserviceclosefailed"></a><span data-ttu-id="24177-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span><span class="sxs-lookup"><span data-stu-id="24177-102">System.ServiceModel.Activation.WebHostServiceCloseFailed</span></span>
<span data-ttu-id="24177-103">Se produit lorsqu'un service ne peut pas être fermé normalement et est abandonné.</span><span class="sxs-lookup"><span data-stu-id="24177-103">Occurs when a service cannot be closed gracefully and is aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="24177-104">Description</span><span class="sxs-lookup"><span data-stu-id="24177-104">Description</span></span>  
 <span data-ttu-id="24177-105">Ce code d'erreur apparaît seulement dans le fichier journal.</span><span class="sxs-lookup"><span data-stu-id="24177-105">This error code only appears in the log file.</span></span> <span data-ttu-id="24177-106">Il indique généralement une erreur de programmation, par exemple lorsque vous essayez de fermer un service après l'appel d'Abort.</span><span class="sxs-lookup"><span data-stu-id="24177-106">It usually indicates a programming error, for example, when you try to close a service after Abort has already been called.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="24177-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="24177-107">Troubleshooting</span></span>  
 <span data-ttu-id="24177-108">Vérifiez le code source de l'application.</span><span class="sxs-lookup"><span data-stu-id="24177-108">Check the application source code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24177-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24177-109">See Also</span></span>  
 [<span data-ttu-id="24177-110">Suivi</span><span class="sxs-lookup"><span data-stu-id="24177-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="24177-111">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="24177-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="24177-112">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="24177-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
