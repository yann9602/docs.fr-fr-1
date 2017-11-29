---
title: "Types déconseillés dans Windows Workflow Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 085b0590d08843477c4dff4754791c93110b1fb7
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="cd127-102">Types déconseillés dans Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="cd127-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="cd127-103">Dans le .NET 4, l'équipe de workflow a mis à disposition un nouveau au moteur de workflow dans l'espace de noms <xref:System.Activities>.</span><span class="sxs-lookup"><span data-stu-id="cd127-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="cd127-104">Avec la version de .NET 4.5 bêta, nous sommes marquant la plupart des types dans le « WF 3 » <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, et <xref:System.Workflow.Runtime> espaces de noms comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="cd127-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="cd127-105">Espaces de noms et outils obsolètes</span><span class="sxs-lookup"><span data-stu-id="cd127-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="cd127-106">Les assemblys suivants ont un ou plusieurs types publics qui seront déconseillés :</span><span class="sxs-lookup"><span data-stu-id="cd127-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="cd127-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="cd127-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="cd127-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="cd127-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="cd127-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="cd127-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="cd127-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="cd127-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="cd127-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="cd127-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="cd127-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="cd127-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="cd127-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="cd127-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="cd127-114">Par conséquent, les clients qui utilisent les API WF 3 déconseillées rencontreront des avertissements de génération avec un message similaire au suivant :</span><span class="sxs-lookup"><span data-stu-id="cd127-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="cd127-115">**Avertissement BC40000 : X est obsolète : types WF 3 sont déconseillés. Utilisez plutôt WF 4.**</span><span class="sxs-lookup"><span data-stu-id="cd127-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="cd127-116">Nous allons supprimer les types du .NET Framework dans une mise en production ultérieure, mais nous n’avons pas encore déterminé cette plage de temps (pas dans la version 4.5).</span><span class="sxs-lookup"><span data-stu-id="cd127-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="cd127-117">Cette étape nous permet de communiquer notre direction à nos clients et leur laisse le temps de migrer vers le nouveau modèle WF4.</span><span class="sxs-lookup"><span data-stu-id="cd127-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="cd127-118">Nous allons, bien entendu, continuer à prendre en charge ces types WF 3 sous le [Microsoft politique de Support](http://aka.ms/MicrosoftSupportLifecycle).</span><span class="sxs-lookup"><span data-stu-id="cd127-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](http://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="cd127-119">Les applications WF3 existantes s'exécutent sans problème sur le .NET 4.5, et [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] prend en charge les solutions WF3 nouvelles et existantes.</span><span class="sxs-lookup"><span data-stu-id="cd127-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="cd127-120">Les types liés aux règles dans l'espace de noms <xref:System.Workflow.Activities.Rules>, qui n'ont pas été remplacés dans WF 4.5, n'ont pas été déconseillés.</span><span class="sxs-lookup"><span data-stu-id="cd127-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="cd127-121">Les clients qui souhaitent migrer leurs applications vers WF 4 trouveront aide dans le [conseils de Migration de flux de travail 4](migration-guidance.md).</span><span class="sxs-lookup"><span data-stu-id="cd127-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
