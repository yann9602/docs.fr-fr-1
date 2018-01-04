---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51374a25ee11b3344e950670cc7882db42d39779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="d43a9-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="d43a9-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="d43a9-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="d43a9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d43a9-104">ID</span><span class="sxs-lookup"><span data-stu-id="d43a9-104">ID</span></span>|<span data-ttu-id="d43a9-105">4208</span><span class="sxs-lookup"><span data-stu-id="d43a9-105">4208</span></span>|  
|<span data-ttu-id="d43a9-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="d43a9-106">Keywords</span></span>|<span data-ttu-id="d43a9-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d43a9-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d43a9-108">Niveau</span><span class="sxs-lookup"><span data-stu-id="d43a9-108">Level</span></span>|<span data-ttu-id="d43a9-109">Information</span><span class="sxs-lookup"><span data-stu-id="d43a9-109">Information</span></span>|  
|<span data-ttu-id="d43a9-110">Canal</span><span class="sxs-lookup"><span data-stu-id="d43a9-110">Channel</span></span>|<span data-ttu-id="d43a9-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="d43a9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d43a9-112">Description</span><span class="sxs-lookup"><span data-stu-id="d43a9-112">Description</span></span>  
 <span data-ttu-id="d43a9-113">Indique que le fournisseur SQL effectue une nouvelle tentative de commande SQL en raison d'une erreur SQL.</span><span class="sxs-lookup"><span data-stu-id="d43a9-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d43a9-114">Message</span><span class="sxs-lookup"><span data-stu-id="d43a9-114">Message</span></span>  
 <span data-ttu-id="d43a9-115">Nouvelle tentative d'exécution d'une commande SQL en raison du numéro d'erreur SQL %1.</span><span class="sxs-lookup"><span data-stu-id="d43a9-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d43a9-116">Détails</span><span class="sxs-lookup"><span data-stu-id="d43a9-116">Details</span></span>  
  
|<span data-ttu-id="d43a9-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d43a9-117">Data Item Name</span></span>|<span data-ttu-id="d43a9-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="d43a9-118">Data Item Type</span></span>|<span data-ttu-id="d43a9-119">Description</span><span class="sxs-lookup"><span data-stu-id="d43a9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d43a9-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="d43a9-120">ErrorNumber</span></span>|<span data-ttu-id="d43a9-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d43a9-121">xs:string</span></span>|<span data-ttu-id="d43a9-122">Numéro d'erreur SQL.</span><span class="sxs-lookup"><span data-stu-id="d43a9-122">The SQL error number.</span></span>|  
|<span data-ttu-id="d43a9-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d43a9-123">AppDomain</span></span>|<span data-ttu-id="d43a9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d43a9-124">xs:string</span></span>|<span data-ttu-id="d43a9-125">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d43a9-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
