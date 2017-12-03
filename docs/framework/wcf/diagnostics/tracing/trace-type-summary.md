---
title: Liste des types de suivis
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1570832e5f179b6d2685ad33fad743c9530bb16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="trace-type-summary"></a><span data-ttu-id="f5030-102">Liste des types de suivis</span><span class="sxs-lookup"><span data-stu-id="f5030-102">Trace Type Summary</span></span>
<span data-ttu-id="f5030-103">[Niveaux de source](http://go.microsoft.com/fwlink/?LinkID=94943) définit différents niveaux de trace : critique, erreur, avertissement, Information et Verbose, et fournit une description de la `ActivityTracing` indicateur qui active ou désactive la sortie de traçage d’événements de transfert de limite et d’activité.</span><span class="sxs-lookup"><span data-stu-id="f5030-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="f5030-104">Vous pouvez également consulter [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) pour les types de suivis qui peuvent être émises à partir de <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="f5030-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="f5030-105">Le tableau suivant répertorie les plus importants.</span><span class="sxs-lookup"><span data-stu-id="f5030-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="f5030-106">Type de suivi</span><span class="sxs-lookup"><span data-stu-id="f5030-106">Trace Type</span></span>|<span data-ttu-id="f5030-107">Description</span><span class="sxs-lookup"><span data-stu-id="f5030-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="f5030-108">Critical</span><span class="sxs-lookup"><span data-stu-id="f5030-108">Critical</span></span>|<span data-ttu-id="f5030-109">Erreur irrécupérable ou panne d'application.</span><span class="sxs-lookup"><span data-stu-id="f5030-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="f5030-110">Erreur</span><span class="sxs-lookup"><span data-stu-id="f5030-110">Error</span></span>|<span data-ttu-id="f5030-111">Erreur récupérable.</span><span class="sxs-lookup"><span data-stu-id="f5030-111">Recoverable error.</span></span>|  
|<span data-ttu-id="f5030-112">Warning</span><span class="sxs-lookup"><span data-stu-id="f5030-112">Warning</span></span>|<span data-ttu-id="f5030-113">Message d'informations.</span><span class="sxs-lookup"><span data-stu-id="f5030-113">Informational message.</span></span>|  
|<span data-ttu-id="f5030-114">Information</span><span class="sxs-lookup"><span data-stu-id="f5030-114">Information</span></span>|<span data-ttu-id="f5030-115">Problème non critique.</span><span class="sxs-lookup"><span data-stu-id="f5030-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="f5030-116">Verbose</span><span class="sxs-lookup"><span data-stu-id="f5030-116">Verbose</span></span>|<span data-ttu-id="f5030-117">Suivi de débogage.</span><span class="sxs-lookup"><span data-stu-id="f5030-117">Debugging trace.</span></span>|  
|<span data-ttu-id="f5030-118">Démarrer</span><span class="sxs-lookup"><span data-stu-id="f5030-118">Start</span></span>|<span data-ttu-id="f5030-119">Démarrage d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="f5030-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="f5030-120">Interrompre</span><span class="sxs-lookup"><span data-stu-id="f5030-120">Suspend</span></span>|<span data-ttu-id="f5030-121">Interruption d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="f5030-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="f5030-122">Reprendre</span><span class="sxs-lookup"><span data-stu-id="f5030-122">Resume</span></span>|<span data-ttu-id="f5030-123">Reprise d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="f5030-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="f5030-124">Arrêter</span><span class="sxs-lookup"><span data-stu-id="f5030-124">Stop</span></span>|<span data-ttu-id="f5030-125">Arrêt d'une unité logique de traitement.</span><span class="sxs-lookup"><span data-stu-id="f5030-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="f5030-126">Transférer</span><span class="sxs-lookup"><span data-stu-id="f5030-126">Transfer</span></span>|<span data-ttu-id="f5030-127">Changement d'identité de corrélation.</span><span class="sxs-lookup"><span data-stu-id="f5030-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="f5030-128">Une activité est définie comme une combinaison des types de suivi ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f5030-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="f5030-129">Le code suivant est une expression régulière qui définit une activité idéale dans une étendue locale (source de suivi).</span><span class="sxs-lookup"><span data-stu-id="f5030-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="f5030-130">Cela signifie qu'une activité doit remplir les conditions suivantes.</span><span class="sxs-lookup"><span data-stu-id="f5030-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="f5030-131">Elle doit respectivement démarrer et s'arrêter avec les suivis Démarrer et Arrêter.</span><span class="sxs-lookup"><span data-stu-id="f5030-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="f5030-132">Elle doit contenir un suivi Transfert immédiatement avant un suivi Interrompre ou Reprendre.</span><span class="sxs-lookup"><span data-stu-id="f5030-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="f5030-133">Elle ne doit pas contenir de suivi entre les suivis Interrompre et Reprendre, s'ils existent.</span><span class="sxs-lookup"><span data-stu-id="f5030-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="f5030-134">Elle peut contenir n'importe quel type de suivi Critique/Avertissement/Informations/Commentaires/Transfert, en nombre illimité, tant que les conditions précédentes sont observées.</span><span class="sxs-lookup"><span data-stu-id="f5030-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="f5030-135">Le code suivant est une expression régulière qui définit une activité idéale dans la portée globale,</span><span class="sxs-lookup"><span data-stu-id="f5030-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="f5030-136">R étant l'expression régulière d'une activité dans l'étendue locale.</span><span class="sxs-lookup"><span data-stu-id="f5030-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="f5030-137">Cela se traduit par :</span><span class="sxs-lookup"><span data-stu-id="f5030-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
