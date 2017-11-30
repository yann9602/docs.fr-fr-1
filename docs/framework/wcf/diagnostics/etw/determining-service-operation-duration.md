---
title: "Détermination de la durée d'une opération de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63a8c92713ee452da2439475ac526229d1e5741c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="determining-service-operation-duration"></a><span data-ttu-id="2b977-102">Détermination de la durée d'une opération de service</span><span class="sxs-lookup"><span data-stu-id="2b977-102">Determining service operation duration</span></span>
<span data-ttu-id="2b977-103">Si le traçage analytique est activé dans une application [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], la durée d'exécution d'une opération de service peut être déterminée facilement en examinant le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="2b977-103">If analytic tracing is enabled in a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application, the duration of execution for a service operation can easily be determined by examining the event log.</span></span>  <span data-ttu-id="2b977-104">Cette rubrique montre comment déterminer la durée d'exécution d'une opération de service.</span><span class="sxs-lookup"><span data-stu-id="2b977-104">This topic demonstrates how to determine the amount of time a service operation takes to complete.</span></span>  
  
### <a name="determining-service-operation-execution-duration"></a><span data-ttu-id="2b977-105">Détermination de la durée d'exécution d'une opération de service</span><span class="sxs-lookup"><span data-stu-id="2b977-105">Determining service operation execution duration</span></span>  
  
1.  <span data-ttu-id="2b977-106">Ouvrez l’Observateur d’événements en cliquant sur **Démarrer**, **exécuter**et en entrant `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="2b977-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="2b977-107">Si vous n’avez pas activé le traçage analytique, développez **journaux des Applications et Services**, **Microsoft**, **Windows**, **serveur d’applications-Applications** .</span><span class="sxs-lookup"><span data-stu-id="2b977-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="2b977-108">Sélectionnez **vue**, **afficher d’analyse et les journaux de débogage**.</span><span class="sxs-lookup"><span data-stu-id="2b977-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="2b977-109">Avec le bouton droit **analyse** et sélectionnez **activer le journal**.</span><span class="sxs-lookup"><span data-stu-id="2b977-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="2b977-110">Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'exécution de l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="2b977-110">Leave Event Viewer open so that traces can be viewed after the service operation is run.</span></span>  
  
3.  <span data-ttu-id="2b977-111">Ouvrez ensuite une application [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] qui inclut un projet de service et un projet client qui interagit avec ce service.</span><span class="sxs-lookup"><span data-stu-id="2b977-111">Next, open a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] application that includes a service project and a client project that interacts with that service.</span></span>  <span data-ttu-id="2b977-112">Vous pouvez créer une telle application en suivant le [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="2b977-112">You can create such an application by following the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  <span data-ttu-id="2b977-113">Si vous avez le [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exemples installés, vous pouvez ouvrir le [mise en route](../../../../../docs/framework/wcf/samples/getting-started-sample.md), qui contient le projet terminé, créé dans le didacticiel.</span><span class="sxs-lookup"><span data-stu-id="2b977-113">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="2b977-114">Exécutez l’application serveur en appuyant sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="2b977-114">Execute the server application by pressing **F5**.</span></span> <span data-ttu-id="2b977-115">Exécutez l’application cliente en cliquant sur le **Client** projet et en sélectionnant **déboguer**, **démarrer une nouvelle Instance**.</span><span class="sxs-lookup"><span data-stu-id="2b977-115">Execute the client application by right-clicking on the **Client** project and selecting **Debug**, **Start New Instance**.</span></span>  
  
5.  <span data-ttu-id="2b977-116">Dans l'Observateur d'événements, actualisez le journal Analyse et triez les événements par ID d'événement.</span><span class="sxs-lookup"><span data-stu-id="2b977-116">In Event Viewer, refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="2b977-117">Recherchez les événements dont l’ID d’événement [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span><span class="sxs-lookup"><span data-stu-id="2b977-117">Look for events with Event ID [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).</span></span>  <span data-ttu-id="2b977-118">Ces événements affichent les opérations terminées et leur durée.</span><span class="sxs-lookup"><span data-stu-id="2b977-118">These events will show which operations have completed, and what the duration of the operation was.</span></span>  <span data-ttu-id="2b977-119">L'événement suivant affiche la durée d'une opération d'ajout.</span><span class="sxs-lookup"><span data-stu-id="2b977-119">The following event shows the duration of an Add operation.</span></span>  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
