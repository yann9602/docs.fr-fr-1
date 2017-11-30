---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61360eff4f2c403eea98bbc0a2eae36e516b3d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="22522-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="22522-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="22522-103">La négociation du protocole OleTransactions n'a pas pu se terminer pour le contexte de coordination spécifié.</span><span class="sxs-lookup"><span data-stu-id="22522-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="22522-104">Description</span><span class="sxs-lookup"><span data-stu-id="22522-104">Description</span></span>  
 <span data-ttu-id="22522-105">Tracé lorsqu'une transaction entrante avec des informations OleTx ne peut pas utiliser les informations OleTx jointes, et a recours à l'utilisation de WS-AT à la place.</span><span class="sxs-lookup"><span data-stu-id="22522-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="22522-106">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="22522-106">Troubleshooting</span></span>  
 <span data-ttu-id="22522-107">Indique un problème potentiel avec la communication de MSDTC RPC entre les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="22522-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="22522-108">Si beaucoup de ces suivis apparaissent dans le journal, il peut s'ensuivre une baisse radicale des performances.</span><span class="sxs-lookup"><span data-stu-id="22522-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="22522-109">Si OleTx n'est pas souhaité, affectez la valeur 0 à `OleTxUpgradeEnabled` dans la configuration du registre WS-AT.</span><span class="sxs-lookup"><span data-stu-id="22522-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22522-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22522-110">See Also</span></span>  
 [<span data-ttu-id="22522-111">Le suivi</span><span class="sxs-lookup"><span data-stu-id="22522-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="22522-112">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="22522-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="22522-113">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="22522-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
