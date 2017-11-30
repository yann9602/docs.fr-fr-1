---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e3cbe9443f32ec9752198646e96cc1012d7343c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="0aaca-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="0aaca-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>
<span data-ttu-id="0aaca-103">Le service de protocole WS-AT n'a pas pu inscrire un participant à un protocole de contrôle.</span><span class="sxs-lookup"><span data-stu-id="0aaca-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0aaca-104">Description</span><span class="sxs-lookup"><span data-stu-id="0aaca-104">Description</span></span>  
 <span data-ttu-id="0aaca-105">Suivi lorsque MSDTC détecte une demande d'inscription non valide.</span><span class="sxs-lookup"><span data-stu-id="0aaca-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="0aaca-106">Cela peut être provoqué par plusieurs demandes d'inscription pour achèvement et erreurs internes.</span><span class="sxs-lookup"><span data-stu-id="0aaca-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0aaca-107">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="0aaca-107">Troubleshooting</span></span>  
 <span data-ttu-id="0aaca-108">Ne procédez pas à plusieurs demandes d'inscription pour achèvement.</span><span class="sxs-lookup"><span data-stu-id="0aaca-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="0aaca-109">Par ailleurs, inspectez la chaîne d'état dans le message de suivi pour déterminer la présence éventuelle d'éléments actionnables.</span><span class="sxs-lookup"><span data-stu-id="0aaca-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aaca-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0aaca-110">See Also</span></span>  
 [<span data-ttu-id="0aaca-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="0aaca-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0aaca-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="0aaca-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0aaca-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="0aaca-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
