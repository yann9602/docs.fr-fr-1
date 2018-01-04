---
title: Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16cb428d-d886-4789-a961-6fded4b0dbba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 960166c7c1d91bcab8420a55e633b461bf37c626
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecoordinatorstatemachinefinished"></a><span data-ttu-id="63d3f-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="63d3f-102">Microsoft.Transactions.TransactionBridge.CoordinatorStateMachineFinished</span></span>
<span data-ttu-id="63d3f-103">La machine à états pour un enrôlement de coordinateur est passée à l'état Finished.</span><span class="sxs-lookup"><span data-stu-id="63d3f-103">The state machine for a coordinator enlistment has entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="63d3f-104">Description</span><span class="sxs-lookup"><span data-stu-id="63d3f-104">Description</span></span>  
 <span data-ttu-id="63d3f-105">Suivi lorsque le gestionnaire de transactions local croit qu’un enrôlement de coordinateur supérieur a terminé le traitement 2PC.</span><span class="sxs-lookup"><span data-stu-id="63d3f-105">Traced when the local Transaction Manager believes a superior coordinator enlistment has completed 2pc processing.</span></span> <span data-ttu-id="63d3f-106">Le résultat peut être Committed, Aborted ou Forgotten.</span><span class="sxs-lookup"><span data-stu-id="63d3f-106">The outcome for the enlistment can be Committed or Aborted or Forgotten.</span></span> <span data-ttu-id="63d3f-107">Suivi également lorsque le gestionnaire de transaction local vote ReadOnly pendant la préparation.</span><span class="sxs-lookup"><span data-stu-id="63d3f-107">It is also traced if the local Transaction Manager votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d3f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63d3f-108">See Also</span></span>  
 [<span data-ttu-id="63d3f-109">Suivi</span><span class="sxs-lookup"><span data-stu-id="63d3f-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="63d3f-110">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="63d3f-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="63d3f-111">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="63d3f-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
