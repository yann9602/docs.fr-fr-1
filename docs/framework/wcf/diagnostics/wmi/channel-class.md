---
title: Channel, classe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 93632d6a178c0f58143fc148a0e1eb51be94ed17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="channel-class"></a><span data-ttu-id="2e666-102">Channel, classe</span><span class="sxs-lookup"><span data-stu-id="2e666-102">Channel class</span></span>
<span data-ttu-id="2e666-103">Canal</span><span class="sxs-lookup"><span data-stu-id="2e666-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e666-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e666-104">Syntax</span></span>  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2e666-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2e666-105">Methods</span></span>  
 <span data-ttu-id="2e666-106">La classe Channel ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="2e666-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2e666-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2e666-107">Properties</span></span>  
 <span data-ttu-id="2e666-108">La classe Channel possède les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="2e666-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="2e666-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="2e666-109">LocalAddress</span></span>  
 <span data-ttu-id="2e666-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="2e666-110">Data type: string</span></span>  
  
 <span data-ttu-id="2e666-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2e666-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e666-112">Point de terminaison local du canal.</span><span class="sxs-lookup"><span data-stu-id="2e666-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="2e666-113">ref</span><span class="sxs-lookup"><span data-stu-id="2e666-113">ref</span></span>  
 <span data-ttu-id="2e666-114">Type de données : point de terminaison</span><span class="sxs-lookup"><span data-stu-id="2e666-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="2e666-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2e666-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e666-116">Référence au point de terminaison auquel le canal se connecte.</span><span class="sxs-lookup"><span data-stu-id="2e666-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="2e666-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="2e666-117">RemoteAddress</span></span>  
 <span data-ttu-id="2e666-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="2e666-118">Data type: string</span></span>  
  
 <span data-ttu-id="2e666-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2e666-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e666-120">Adresse distante associée au canal.</span><span class="sxs-lookup"><span data-stu-id="2e666-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="2e666-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="2e666-121">SessionId</span></span>  
 <span data-ttu-id="2e666-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="2e666-122">Data type: string</span></span>  
  
 <span data-ttu-id="2e666-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2e666-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e666-124">Id de session actuel, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="2e666-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="2e666-125">Type</span><span class="sxs-lookup"><span data-stu-id="2e666-125">Type</span></span>  
 <span data-ttu-id="2e666-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="2e666-126">Data type: string</span></span>  
  
 <span data-ttu-id="2e666-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="2e666-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e666-128">Type du canal.</span><span class="sxs-lookup"><span data-stu-id="2e666-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e666-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2e666-129">Requirements</span></span>  
  
|<span data-ttu-id="2e666-130">MOF</span><span class="sxs-lookup"><span data-stu-id="2e666-130">MOF</span></span>|<span data-ttu-id="2e666-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2e666-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2e666-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="2e666-132">Namespace</span></span>|<span data-ttu-id="2e666-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2e666-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e666-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e666-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
