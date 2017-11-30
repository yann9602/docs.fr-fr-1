---
title: "Événements ETW dans le Common Language Runtime"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8313a6b06387f6fd0a5f95191ea57bdf034c372
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="etw-events-in-the-common-language-runtime"></a><span data-ttu-id="76110-102">Événements ETW dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="76110-102">ETW Events in the Common Language Runtime</span></span>
<span data-ttu-id="76110-103">Le CLR (Common Language Runtime) fournit des informations de diagnostic utiles pour le suivi d’événements pour Windows (ETW) par le biais d’une grande variété d’événements de débogage et de profilage.</span><span class="sxs-lookup"><span data-stu-id="76110-103">The common language runtime (CLR) provides useful event tracing for Windows (ETW) diagnostic information through a large variety of debugging and profiling events.</span></span> <span data-ttu-id="76110-104">Les événements ETW du CLR tirent parti du système de suivi Windows (ETW) pour améliorer la prise en charge du profilage et du débogage déjà proposée par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="76110-104">CLR ETW events leverage the Windows ETW tracing system to augment the existing profiling and debugging support provided by the common language runtime.</span></span>  
  
 <span data-ttu-id="76110-105">Vous trouverez des informations supplémentaires sur ETW dans l’article [Améliorez le débogage et l’optimisation des performances avec ETW](http://go.microsoft.com/fwlink/?LinkID=161142) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="76110-105">More information about ETW is available in the article [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkID=161142) on MSDN.</span></span> <span data-ttu-id="76110-106">Des informations relatives à Xperf sont disponibles à la page [Windows Performance Toolkit - Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) du blog NTDebugging.</span><span class="sxs-lookup"><span data-stu-id="76110-106">Information about Xperf can be found in the entry [Windows Performance Toolkit - Xperf](http://go.microsoft.com/fwlink/?LinkID=161144) in the NTDebugging blog.</span></span>  
  
 <span data-ttu-id="76110-107">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] ou version ultérieure est nécessaire pour tous les événements décrits dans les rubriques d’événements.</span><span class="sxs-lookup"><span data-stu-id="76110-107">The [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later is required for all the events described in the event topics.</span></span> <span data-ttu-id="76110-108">Le système d’exploitation Windows Vista est le client minimal pris en charge, et Windows Server 2008 est le serveur minimal pris en charge.</span><span class="sxs-lookup"><span data-stu-id="76110-108">The Windows Vista operating system is the minimum supported client, and Windows Server 2008 is the minimum supported server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76110-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="76110-109">In This Section</span></span>  
 [<span data-ttu-id="76110-110">Contrôle de l’enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="76110-110">Controlling .NET Framework Logging</span></span>](../../../docs/framework/performance/controlling-logging.md)  
 <span data-ttu-id="76110-111">Décrit les outils et les commandes permettant de capturer et d’afficher des événements ETW.</span><span class="sxs-lookup"><span data-stu-id="76110-111">Describes the tools and commands for capturing and viewing ETW events.</span></span>  
  
 [<span data-ttu-id="76110-112">Fournisseurs ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="76110-112">CLR ETW Providers</span></span>](../../../docs/framework/performance/clr-etw-providers.md)  
 <span data-ttu-id="76110-113">Fournit des informations sur les fournisseurs d’arrêt et de runtime, et sur la façon de les utiliser pour collecter des données ETW.</span><span class="sxs-lookup"><span data-stu-id="76110-113">Provides information about the runtime and rundown providers, and how you can use them for ETW data collection.</span></span>  
  
 [<span data-ttu-id="76110-114">Niveaux et mots clés ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="76110-114">CLR ETW Keywords and Levels</span></span>](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 <span data-ttu-id="76110-115">Décrit les mots clés pour les fournisseurs d’arrêt et de runtime qui permettent de filtrer des événements par catégorie.</span><span class="sxs-lookup"><span data-stu-id="76110-115">Describes the keywords for the Runtime and Rundown providers that enable the filtering of events by category.</span></span>  
  
 [<span data-ttu-id="76110-116">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="76110-116">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)  
 <span data-ttu-id="76110-117">Fournit des informations détaillées sur les événements ETW du CLR, leurs mots clés, leurs niveaux et leurs données d’événement.</span><span class="sxs-lookup"><span data-stu-id="76110-117">Provides detailed information about CLR ETW events, their keywords, levels, and event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76110-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76110-118">See Also</span></span>  
 [<span data-ttu-id="76110-119">Événements ETW dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="76110-119">ETW Events in the .NET Framework</span></span>](../../../docs/framework/performance/etw-events.md)
