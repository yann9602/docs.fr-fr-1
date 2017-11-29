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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1df634a61cce695fca74fdfe53beea6c0f83d082
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="channel-class"></a><span data-ttu-id="e359f-102">Channel, classe</span><span class="sxs-lookup"><span data-stu-id="e359f-102">Channel class</span></span>
<span data-ttu-id="e359f-103">Canal</span><span class="sxs-lookup"><span data-stu-id="e359f-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e359f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e359f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e359f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e359f-105">Methods</span></span>  
 <span data-ttu-id="e359f-106">La classe Channel ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="e359f-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e359f-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e359f-107">Properties</span></span>  
 <span data-ttu-id="e359f-108">La classe Channel possède les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="e359f-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="e359f-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="e359f-109">LocalAddress</span></span>  
 <span data-ttu-id="e359f-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e359f-110">Data type: string</span></span>  
  
 <span data-ttu-id="e359f-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e359f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e359f-112">Point de terminaison local du canal.</span><span class="sxs-lookup"><span data-stu-id="e359f-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e359f-113">ref</span><span class="sxs-lookup"><span data-stu-id="e359f-113">ref</span></span>  
 <span data-ttu-id="e359f-114">Type de données : point de terminaison</span><span class="sxs-lookup"><span data-stu-id="e359f-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="e359f-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e359f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e359f-116">Référence au point de terminaison auquel le canal se connecte.</span><span class="sxs-lookup"><span data-stu-id="e359f-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="e359f-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="e359f-117">RemoteAddress</span></span>  
 <span data-ttu-id="e359f-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e359f-118">Data type: string</span></span>  
  
 <span data-ttu-id="e359f-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e359f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e359f-120">Adresse distante associée au canal.</span><span class="sxs-lookup"><span data-stu-id="e359f-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="e359f-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="e359f-121">SessionId</span></span>  
 <span data-ttu-id="e359f-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e359f-122">Data type: string</span></span>  
  
 <span data-ttu-id="e359f-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e359f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e359f-124">Id de session actuel, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="e359f-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="e359f-125">Type</span><span class="sxs-lookup"><span data-stu-id="e359f-125">Type</span></span>  
 <span data-ttu-id="e359f-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e359f-126">Data type: string</span></span>  
  
 <span data-ttu-id="e359f-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e359f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e359f-128">Type du canal.</span><span class="sxs-lookup"><span data-stu-id="e359f-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e359f-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e359f-129">Requirements</span></span>  
  
|<span data-ttu-id="e359f-130">MOF</span><span class="sxs-lookup"><span data-stu-id="e359f-130">MOF</span></span>|<span data-ttu-id="e359f-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e359f-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e359f-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e359f-132">Namespace</span></span>|<span data-ttu-id="e359f-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e359f-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e359f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e359f-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
