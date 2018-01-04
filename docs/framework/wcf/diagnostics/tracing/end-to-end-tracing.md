---
title: Suivi de bout en bout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8a2127c8dda26c376d7d722a24d72d2330174027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="93f03-102">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="93f03-102">End-to-End Tracing</span></span>
<span data-ttu-id="93f03-103">Le suivi de bout en bout (e2e) permet aux développeurs de suivre l'exécution du code dans l'infrastructure [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] pour examiner pourquoi un chemin de code a échoué, ou d'assurer le suivi détaillé pour la planification de la capacité et l'analyse des performances.</span><span class="sxs-lookup"><span data-stu-id="93f03-103">End to End (e2e) Tracing allows developers to follow the execution of code in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="93f03-104"> fournit trois mécanismes de corrélation qui facilitent l'identification de la cause d'une erreur : activités, transferts et propagation.</span><span class="sxs-lookup"><span data-stu-id="93f03-104"> provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="93f03-105">Consultez [les scénarios de suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) pour obtenir la liste de scénarios de suivi de bout en bout et leur activité correspondante et le suivi de conception.</span><span class="sxs-lookup"><span data-stu-id="93f03-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93f03-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="93f03-106">In This Section</span></span>  
 <span data-ttu-id="93f03-107">[Activité](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md): décrit les suivis d’activité dans le [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="93f03-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
 <span data-ttu-id="93f03-108">[Transfert](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md): décrit le transfert dans la [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modèle de suivi et à l’aide de transfert pour corréler des activités au sein des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="93f03-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="93f03-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md): décrit la propagation d’activité dans le [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] le modèle de suivi et à l’aide de la propagation pour corréler des activités sur les points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="93f03-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="93f03-110">Liste des types de suivis</span><span class="sxs-lookup"><span data-stu-id="93f03-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="93f03-111">Fournit un résumé de tous les types de suivi d'activité</span><span class="sxs-lookup"><span data-stu-id="93f03-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f03-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93f03-112">See Also</span></span>  
 [<span data-ttu-id="93f03-113">Configuration du suivi</span><span class="sxs-lookup"><span data-stu-id="93f03-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="93f03-114">Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="93f03-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="93f03-115">Scénarios de suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="93f03-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="93f03-116">Outil Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="93f03-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
