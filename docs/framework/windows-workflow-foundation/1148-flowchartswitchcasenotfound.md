---
title: 1148 - FlowchartSwitchCaseNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fa173290b528be690b418622baaa2a12e4930cb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="1148---flowchartswitchcasenotfound"></a><span data-ttu-id="f0f90-102">1148 - FlowchartSwitchCaseNotFound</span><span class="sxs-lookup"><span data-stu-id="f0f90-102">1148 - FlowchartSwitchCaseNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="f0f90-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f0f90-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0f90-104">ID</span><span class="sxs-lookup"><span data-stu-id="f0f90-104">ID</span></span>|<span data-ttu-id="f0f90-105">1148</span><span class="sxs-lookup"><span data-stu-id="f0f90-105">1148</span></span>|  
|<span data-ttu-id="f0f90-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f0f90-106">Keywords</span></span>|<span data-ttu-id="f0f90-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="f0f90-107">WFActivities</span></span>|  
|<span data-ttu-id="f0f90-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="f0f90-108">Level</span></span>|<span data-ttu-id="f0f90-109">Information</span><span class="sxs-lookup"><span data-stu-id="f0f90-109">Information</span></span>|  
|<span data-ttu-id="f0f90-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f0f90-110">Channel</span></span>|<span data-ttu-id="f0f90-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="f0f90-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f0f90-112">Description</span><span class="sxs-lookup"><span data-stu-id="f0f90-112">Description</span></span>  
 <span data-ttu-id="f0f90-113">Indique qu'une correspondance de cas ou un cas par défaut est introuvable dans un organigramme.</span><span class="sxs-lookup"><span data-stu-id="f0f90-113">Indicates that neither a matching case or a default case in a Flowchart switch could be found.</span></span> <span data-ttu-id="f0f90-114">L'exécution de Flowchart va se terminer.</span><span class="sxs-lookup"><span data-stu-id="f0f90-114">Flowchart execution will end.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f0f90-115">Message</span><span class="sxs-lookup"><span data-stu-id="f0f90-115">Message</span></span>  
 <span data-ttu-id="f0f90-116">Flowchart « %1 »/FlowSwitch - impossible de trouver l'activité Case ou un cas par défaut correspondant au résultat de l'expression.</span><span class="sxs-lookup"><span data-stu-id="f0f90-116">Flowchart '%1'/FlowSwitch - could find neither a Case activity nor a Default Case matching the Expression result.</span></span> <span data-ttu-id="f0f90-117">L'exécution de Flowchart va se terminer.</span><span class="sxs-lookup"><span data-stu-id="f0f90-117">Flowchart execution will end.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f0f90-118">Détails</span><span class="sxs-lookup"><span data-stu-id="f0f90-118">Details</span></span>  
  
|<span data-ttu-id="f0f90-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f0f90-119">Data Item Name</span></span>|<span data-ttu-id="f0f90-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f0f90-120">Data Item Type</span></span>|<span data-ttu-id="f0f90-121">Description</span><span class="sxs-lookup"><span data-stu-id="f0f90-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f0f90-122">Organigramme</span><span class="sxs-lookup"><span data-stu-id="f0f90-122">FlowChart</span></span>|<span data-ttu-id="f0f90-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0f90-123">xs:string</span></span>|<span data-ttu-id="f0f90-124">Nom complet de l'organigramme.</span><span class="sxs-lookup"><span data-stu-id="f0f90-124">The display name of the FlowChart.</span></span>|  
|<span data-ttu-id="f0f90-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f0f90-125">AppDomain</span></span>|<span data-ttu-id="f0f90-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="f0f90-126">xs:string</span></span>|<span data-ttu-id="f0f90-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f0f90-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
