---
title: Fournisseurs ETW du CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW, CLR providers
- CLR ETW providers
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 18353939108d58eb2aaffee97e059e4430b25e3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clr-etw-providers"></a><span data-ttu-id="73e3e-102">Fournisseurs ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="73e3e-102">CLR ETW Providers</span></span>
<span data-ttu-id="73e3e-103">Le Common Language Runtime (CLR) a deux fournisseurs : le fournisseur de runtime et le fournisseur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="73e3e-103">The common language runtime (CLR) has two providers: the runtime provider and the rundown provider.</span></span>  
  
 <span data-ttu-id="73e3e-104">Le fournisseur de runtime déclenche des événements en fonction des mots clés (catégories d’événements) activés.</span><span class="sxs-lookup"><span data-stu-id="73e3e-104">The runtime provider raises events, depending on which keywords (categories of events) are enabled.</span></span> <span data-ttu-id="73e3e-105">Par exemple, vous pouvez collecter des événements de chargeur en activant le mot clé `LoaderKeyword`.</span><span class="sxs-lookup"><span data-stu-id="73e3e-105">For example, you can collect loader events by enabling the `LoaderKeyword` keyword.</span></span>  
  
 <span data-ttu-id="73e3e-106">Les événements ETW (suivi des événements Windows) sont journalisés dans un fichier comportant l’extension .etl, qui peut être post-traité ultérieurement dans des fichiers de valeurs séparées par des virgules (.csv), si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="73e3e-106">Event tracking for Windows (ETW) events are logged into a file that has an .etl extension, which can later be post-processed in comma-separated value (.csv) files as needed.</span></span> <span data-ttu-id="73e3e-107">Pour plus d’informations sur la façon de convertir le fichier .etl en fichier .csv, consultez [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md) (Contrôle de la journalisation du .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="73e3e-107">For information about how to convert the .etl file to a .csv file, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="the-runtime-provider"></a><span data-ttu-id="73e3e-108">Fournisseur de runtime</span><span class="sxs-lookup"><span data-stu-id="73e3e-108">The Runtime Provider</span></span>  
 <span data-ttu-id="73e3e-109">Le fournisseur de runtime est le principal fournisseur ETW du CLR.</span><span class="sxs-lookup"><span data-stu-id="73e3e-109">The runtime provider is the main CLR ETW provider.</span></span>  
  
 <span data-ttu-id="73e3e-110">Le GUID du fournisseur de runtime du CLR est e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span><span class="sxs-lookup"><span data-stu-id="73e3e-110">The CLR runtime provider GUID is e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.</span></span>  
  
 <span data-ttu-id="73e3e-111">Pour obtenir des exemples de journalisation et d’affichage des événements ETW du CLR à l’aide d’outils courants, consultez [Contrôle de la journalisation du .NET Framework](../../../docs/framework/performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="73e3e-111">For examples of how to log and view CLR ETW events by using commonly available tools, see [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
 <span data-ttu-id="73e3e-112">En plus des mots clés tels que `LoaderKeyword`, vous devrez éventuellement activer des mots clés pour la journalisation des événements qui se déclenchent trop fréquemment.</span><span class="sxs-lookup"><span data-stu-id="73e3e-112">In addition to using keywords such as `LoaderKeyword`, you may have to enable keywords for logging events that may be raised too frequently.</span></span> <span data-ttu-id="73e3e-113">Les mots clés `StartEnumerationKeyword` et `EndEnumerationKeyword` activent ces événements et sont résumés dans [Mots clés et niveaux CLR ETW](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="73e3e-113">The `StartEnumerationKeyword` and the `EndEnumerationKeyword` keywords enable these events and are summarized in [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).</span></span>  
  
## <a name="the-rundown-provider"></a><span data-ttu-id="73e3e-114">Fournisseur d’arrêt</span><span class="sxs-lookup"><span data-stu-id="73e3e-114">The Rundown Provider</span></span>  
 <span data-ttu-id="73e3e-115">Le fournisseur d’arrêt doit être activé dans certains cas bien précis.</span><span class="sxs-lookup"><span data-stu-id="73e3e-115">The rundown provider must be turned on for certain special-purpose uses.</span></span> <span data-ttu-id="73e3e-116">Toutefois, pour la plupart des utilisateurs, le fournisseur de runtime est tout à fait suffisant.</span><span class="sxs-lookup"><span data-stu-id="73e3e-116">However, for a majority of users, the runtime provider should suffice.</span></span>  
  
 <span data-ttu-id="73e3e-117">Le GUID du fournisseur d’arrêt du CLR est A669021C-C450-4609-A035-5AF59AF4DF18.</span><span class="sxs-lookup"><span data-stu-id="73e3e-117">The CLR rundown provider GUID is A669021C-C450-4609-A035-5AF59AF4DF18.</span></span>  
  
 <span data-ttu-id="73e3e-118">Normalement, la journalisation ETW est activée avant le lancement d’un processus et désactivée une fois ce processus arrêté.</span><span class="sxs-lookup"><span data-stu-id="73e3e-118">Normally, ETW logging is enabled before a process launches, and the logging is turned off after the process exits.</span></span> <span data-ttu-id="73e3e-119">Toutefois, si la journalisation ETW est activée pendant l’exécution du processus, des informations supplémentaires sur celui-ci sont demandées.</span><span class="sxs-lookup"><span data-stu-id="73e3e-119">However, if ETW logging is turned on while the process is executing, additional information is needed about the process.</span></span> <span data-ttu-id="73e3e-120">Par exemple, pour la résolution des symboles, vous devez journaliser les événements de méthode pour les méthodes qui ont été chargées avant l’activation de la journalisation.</span><span class="sxs-lookup"><span data-stu-id="73e3e-120">For example, for symbol resolution you have to log method events for methods that were already loaded before logging was turned on.</span></span>  
  
 <span data-ttu-id="73e3e-121">Les événements `DCStart` et `DCEnd` capturent l’état du processus au moment où la collecte de données a commencé et où elle s’est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="73e3e-121">The `DCStart` and `DCEnd` events capture the state of the process when data collection was started and stopped.</span></span> <span data-ttu-id="73e3e-122">(L’état fait référence aux informations de haut niveau, notamment les méthodes qui étaient déjà compilées juste-à-temps (JIT) et les assemblys déjà chargés.) Ces deux événements peuvent fournir des informations sur ce qui s’est déjà produit dans le processus, par exemple quelles méthodes ont été compilées juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="73e3e-122">(State refers to information at a high level, including the methods that were already just-in-time (JIT) compiled and assemblies that were loaded.) These two events can provide information about what has already happened in the process; for example, which methods were JIT- compiled, and so on.</span></span>  
  
 <span data-ttu-id="73e3e-123">Seuls les événements dont le nom contient `DC`, `DCStart`, `DCEnd` ou `DCInit` sont déclenchés sous le fournisseur d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="73e3e-123">Only the events with `DC`, `DCStart`, `DCEnd`, or `DCInit` in their names are raised under the rundown provider.</span></span> <span data-ttu-id="73e3e-124">Par ailleurs, ces événements sont déclenchés uniquement sous ce fournisseur.</span><span class="sxs-lookup"><span data-stu-id="73e3e-124">Additionally, these events are raised only under the rundown provider.</span></span>  
  
 <span data-ttu-id="73e3e-125">En plus des filtres par mots clés d’événement, le fournisseur d’arrêt prend en charge les mots clés `StartRundownKeyword` et `EndRundownKeyword` pour permettre un filtrage ciblé.</span><span class="sxs-lookup"><span data-stu-id="73e3e-125">In addition to the event keyword filters, the rundown provider also supports the `StartRundownKeyword` and `EndRundownKeyword` keywords to provide targeted filtering.</span></span>  
  
### <a name="start-rundown"></a><span data-ttu-id="73e3e-126">Arrêt de début</span><span class="sxs-lookup"><span data-stu-id="73e3e-126">Start Rundown</span></span>  
 <span data-ttu-id="73e3e-127">Un arrêt de début est déclenché quand la journalisation sous le fournisseur d’arrêt est activée avec le mot clé `StartRundownKeyword`.</span><span class="sxs-lookup"><span data-stu-id="73e3e-127">A start rundown is triggered when logging under the rundown provider is enabled with the `StartRundownKeyword` keyword.</span></span> <span data-ttu-id="73e3e-128">Cela entraîne le déclenchement de l’événement `DCStart` et la capture de l’état du système.</span><span class="sxs-lookup"><span data-stu-id="73e3e-128">This causes the `DCStart` event to be raised, and captures the state of the system.</span></span> <span data-ttu-id="73e3e-129">Avant le démarrage de l’énumération, l’événement `DCStartInit` est déclenché.</span><span class="sxs-lookup"><span data-stu-id="73e3e-129">Before the start of the enumeration, the `DCStartInit` event is raised.</span></span> <span data-ttu-id="73e3e-130">À la fin de l’énumération, l’événement `DCStartComplete` est déclenché pour indiquer au contrôleur que la collecte de données s’est terminée normalement.</span><span class="sxs-lookup"><span data-stu-id="73e3e-130">At the end of the enumeration, the `DCStartComplete` event is raised to notify the controller that data collection terminated normally.</span></span>  
  
### <a name="end-rundown"></a><span data-ttu-id="73e3e-131">Arrêt de fin</span><span class="sxs-lookup"><span data-stu-id="73e3e-131">End Rundown</span></span>  
 <span data-ttu-id="73e3e-132">Un arrêt de fin est déclenché quand la journalisation sous le fournisseur d’arrêt est activée avec le mot clé `EndRundownKeyword`.</span><span class="sxs-lookup"><span data-stu-id="73e3e-132">An end rundown is triggered when logging under the rundown provider is enabled with the `EndRundownKeyword` keyword.</span></span> <span data-ttu-id="73e3e-133">L’arrêt de fin arrête le profilage sur un processus qui continue de s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="73e3e-133">End rundown stops profiling on a process that continues to execute.</span></span> <span data-ttu-id="73e3e-134">Les événements `DCEnd` capturent l’état du système quand le profilage est arrêté.</span><span class="sxs-lookup"><span data-stu-id="73e3e-134">The `DCEnd` events capture the state of the system when profiling is stopped.</span></span>  
  
 <span data-ttu-id="73e3e-135">Avant le démarrage de l’énumération, l’événement `DCEndInit` est déclenché.</span><span class="sxs-lookup"><span data-stu-id="73e3e-135">Before the start of the enumeration, the `DCEndInit` event is raised.</span></span> <span data-ttu-id="73e3e-136">À la fin de l’énumération, l’événement `DCEndComplete` est déclenché pour indiquer au consommateur que la collecte de données s’est terminée normalement.</span><span class="sxs-lookup"><span data-stu-id="73e3e-136">At the end of the enumeration, the `DCEndComplete` event is raised to notify the consumer that data collection terminated normally.</span></span> <span data-ttu-id="73e3e-137">Les arrêts de début et de fin sont principalement utilisés pour la résolution de symboles managés.</span><span class="sxs-lookup"><span data-stu-id="73e3e-137">Start rundown and end rundown are primarily used for managed symbol resolution.</span></span> <span data-ttu-id="73e3e-138">L’arrêt de début peut fournir des informations sur les plages d’adresses des méthodes qui ont été compilées juste-à-temps (JIT) avant le début de la session de profilage.</span><span class="sxs-lookup"><span data-stu-id="73e3e-138">Start rundown can provide address range information for methods that were already JIT-compiled before the profiling session was started.</span></span> <span data-ttu-id="73e3e-139">L’arrêt de fin peut fournir des informations sur les plages d’adresses de toutes les méthodes qui ont été compilées juste-à-temps (JIT) quand le profilage est sur le point d’être désactivé.</span><span class="sxs-lookup"><span data-stu-id="73e3e-139">End rundown can provide address range information for all methods that have been JIT-compiled when profiling is about to be turned off.</span></span>  
  
 <span data-ttu-id="73e3e-140">L’arrêt de fin ne se produit pas automatiquement quand une session de profilage est arrêtée.</span><span class="sxs-lookup"><span data-stu-id="73e3e-140">End rundown does not happen automatically when a profiling session is stopped.</span></span> <span data-ttu-id="73e3e-141">Au lieu de cela, un outil qui cherche à exécuter la résolution de symboles managés doit appeler explicitement une session du fournisseur d’arrêt du CLR avec le mot clé `EndRundownKeyword` activé, juste avant l’arrêt du profilage.</span><span class="sxs-lookup"><span data-stu-id="73e3e-141">Instead, a tool that is seeking to perform managed symbol resolution has to explicitly invoke a CLR rundown provider session with the `EndRundownKeyword` keyword enabled, just before profiling is stopped.</span></span>  
  
 <span data-ttu-id="73e3e-142">Bien que l’arrêt de début ou de fin puisse fournir des informations de plage d’adresses de méthodes pour la résolution de symboles managés, nous vous recommandons d’utiliser le mot clé `EndRundownKeyword` (qui fournit des événements `DCEnd`) plutôt que le mot clé `StartRundownKeyword` (qui fournit des événements `DCStart`).</span><span class="sxs-lookup"><span data-stu-id="73e3e-142">Although either start rundown or end rundown can provide method address range information for managed symbol resolution, we recommend that you use the `EndRundownKeyword` keyword (which supplies `DCEnd` events) instead of the `StartRundownKeyword` keyword (which supplies `DCStart` events).</span></span> <span data-ttu-id="73e3e-143">L’utilisation de `StartRundownKeyword` entraîne l’arrêt de la session de profilage, ce qui peut perturber le scénario profilé.</span><span class="sxs-lookup"><span data-stu-id="73e3e-143">Using `StartRundownKeyword` causes the rundown to happen during the profiling session, which may disturb the profiled scenario.</span></span>  
  
## <a name="etw-data-collection-using-runtime-and-rundown-providers"></a><span data-ttu-id="73e3e-144">Collecte de données ETW à l’aide des fournisseurs de runtime et d’arrêt</span><span class="sxs-lookup"><span data-stu-id="73e3e-144">ETW Data Collection Using Runtime and Rundown Providers</span></span>  
 <span data-ttu-id="73e3e-145">L’exemple suivant montre comment utiliser le fournisseur d’arrêt du CLR d’une façon qui autorise la résolution des symboles des processus managés avec un impact minimal, indépendamment du fait que les processus démarrent ou se terminent à l’intérieur ou à l’extérieur de la fenêtre profilée.</span><span class="sxs-lookup"><span data-stu-id="73e3e-145">The following example demonstrates how to use the CLR rundown provider in a way that allows symbol resolution of managed processes with minimal impact, regardless of whether the processes start or end inside or outside the profiled window.</span></span>  
  
1.  <span data-ttu-id="73e3e-146">Activez la journalisation ETW à l’aide du fournisseur de runtime du CLR :</span><span class="sxs-lookup"><span data-stu-id="73e3e-146">Turn on ETW logging by using the CLR runtime provider:</span></span>  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     <span data-ttu-id="73e3e-147">Le journal sera enregistré dans le fichier clr1.etl.</span><span class="sxs-lookup"><span data-stu-id="73e3e-147">The log will be saved to the clr1.etl file.</span></span>  
  
2.  <span data-ttu-id="73e3e-148">Pour arrêter le profilage alors que le processus continue à s’exécuter, démarrez le fournisseur d’arrêt pour capturer les événements `DCEnd` :</span><span class="sxs-lookup"><span data-stu-id="73e3e-148">To stop profiling while the process continues to execute, start the rundown provider to capture the `DCEnd` events:</span></span>  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     <span data-ttu-id="73e3e-149">Cela permet à la collecte d’événements `DCEnd` de démarrer une session d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="73e3e-149">This enables the collection of `DCEnd` events to start a rundown session.</span></span> <span data-ttu-id="73e3e-150">Vous devrez peut-être patienter 30 à 60 secondes pour que tous les événements soient collectés.</span><span class="sxs-lookup"><span data-stu-id="73e3e-150">You may need to wait 30 to 60 seconds for all events to be collected.</span></span> <span data-ttu-id="73e3e-151">Le journal sera enregistré dans le fichier clr1.et2.</span><span class="sxs-lookup"><span data-stu-id="73e3e-151">The log will be saved to the clr1.et2 file.</span></span>  
  
3.  <span data-ttu-id="73e3e-152">Désactivez tout le profilage ETW :</span><span class="sxs-lookup"><span data-stu-id="73e3e-152">Turn off all ETW profiling:</span></span>  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  <span data-ttu-id="73e3e-153">Fusionnez les profils pour créer un fichier journal :</span><span class="sxs-lookup"><span data-stu-id="73e3e-153">Merge the profiles to create one log file:</span></span>  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     <span data-ttu-id="73e3e-154">Le fichier merged.etl contient les événements des sessions des fournisseurs de runtime et d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="73e3e-154">The merged.etl file will contain the events from the runtime and the rundown provider sessions.</span></span>  
  
 <span data-ttu-id="73e3e-155">Un outil peut exécuter les étapes 2 et 3 (démarrage d’une session d’arrêt, puis arrêt du profilage) au lieu de désactiver immédiatement le profilage quand un utilisateur demande son arrêt.</span><span class="sxs-lookup"><span data-stu-id="73e3e-155">A tool can execute steps 2 and 3 (starting a rundown session and then terminating profiling) instead of immediately turning off profiling when a user requests profiling to be stopped.</span></span> <span data-ttu-id="73e3e-156">Un outil peut également exécuter l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="73e3e-156">A tool can also execute step 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e3e-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73e3e-157">See Also</span></span>  
 [<span data-ttu-id="73e3e-158">Événements ETW dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="73e3e-158">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
