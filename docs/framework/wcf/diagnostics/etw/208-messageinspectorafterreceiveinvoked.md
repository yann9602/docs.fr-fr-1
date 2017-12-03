---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 670650c612ac01ab9c82028388a4524d2f08fd79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="9a547-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="9a547-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="9a547-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9a547-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a547-104">ID</span><span class="sxs-lookup"><span data-stu-id="9a547-104">ID</span></span>|<span data-ttu-id="9a547-105">208</span><span class="sxs-lookup"><span data-stu-id="9a547-105">208</span></span>|  
|<span data-ttu-id="9a547-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9a547-106">Keywords</span></span>|<span data-ttu-id="9a547-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a547-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9a547-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="9a547-108">Level</span></span>|<span data-ttu-id="9a547-109">Information</span><span class="sxs-lookup"><span data-stu-id="9a547-109">Information</span></span>|  
|<span data-ttu-id="9a547-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9a547-110">Channel</span></span>|<span data-ttu-id="9a547-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="9a547-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a547-112">Description</span><span class="sxs-lookup"><span data-stu-id="9a547-112">Description</span></span>  
 <span data-ttu-id="9a547-113">Cet événement est émis après que le modèle de service a appelé la méthode `AfterReceive` sur un inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="9a547-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a547-114">Message</span><span class="sxs-lookup"><span data-stu-id="9a547-114">Message</span></span>  
 <span data-ttu-id="9a547-115">Le répartiteur a appelé 'AfterReceiveReply' sur un MessageInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="9a547-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a547-116">Détails</span><span class="sxs-lookup"><span data-stu-id="9a547-116">Details</span></span>  
  
|<span data-ttu-id="9a547-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9a547-117">Data Item Name</span></span>|<span data-ttu-id="9a547-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9a547-118">Data Item Type</span></span>|<span data-ttu-id="9a547-119">Description</span><span class="sxs-lookup"><span data-stu-id="9a547-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a547-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="9a547-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="9a547-121">CLR FullName du type de `MessageInspector` appelé.</span><span class="sxs-lookup"><span data-stu-id="9a547-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="9a547-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="9a547-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="9a547-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="9a547-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9a547-124">Son format est défini en tant que ' chemin d’accès virtuel de Site Web de nom d’Application &#124; Chemin d’accès virtuel de service &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="9a547-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9a547-125">Exemple : ' Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="9a547-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9a547-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a547-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9a547-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9a547-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
