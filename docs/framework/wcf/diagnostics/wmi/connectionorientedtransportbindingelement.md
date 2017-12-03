---
title: ConnectionOrientedTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42974d0f1de639370d6fac2346572758e1d19d46
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="e92c1-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e92c1-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="e92c1-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e92c1-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e92c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e92c1-104">Syntax</span></span>  
  
```  
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e92c1-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e92c1-105">Methods</span></span>  
 <span data-ttu-id="e92c1-106">La classe ConnectionOrientedTransportBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="e92c1-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e92c1-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="e92c1-107">Properties</span></span>  
 <span data-ttu-id="e92c1-108">La classe ConnectionOrientedTransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="e92c1-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="e92c1-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="e92c1-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="e92c1-110">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="e92c1-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="e92c1-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-112">Le timespan qui spécifie le délai d'initialisation du canal avant expiration.</span><span class="sxs-lookup"><span data-stu-id="e92c1-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="e92c1-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="e92c1-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="e92c1-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="e92c1-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e92c1-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-116">Taille de la mémoire tampon utilisée pour transmettre une portion du message sérialisé sur le câble du client ou du service.</span><span class="sxs-lookup"><span data-stu-id="e92c1-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="e92c1-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="e92c1-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="e92c1-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e92c1-118">Data type: string</span></span>  
  
 <span data-ttu-id="e92c1-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-120">Valeur qui indique si le nom d'hôte est utilisé pour atteindre le service lors de la correspondance avec l'URI.</span><span class="sxs-lookup"><span data-stu-id="e92c1-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="e92c1-121">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="e92c1-121">MaxBufferSize</span></span>  
 <span data-ttu-id="e92c1-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="e92c1-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e92c1-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-124">Taille maximale autorisée de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="e92c1-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="e92c1-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="e92c1-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="e92c1-126">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="e92c1-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="e92c1-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-128">Durée maximale pendant laquelle une portion d'un message ou un message complet peut rester en mémoire tampon avant d'être expédié.</span><span class="sxs-lookup"><span data-stu-id="e92c1-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="e92c1-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="e92c1-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="e92c1-130">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="e92c1-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="e92c1-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-132">Nombre maximal de threads d'acceptation asynchrones en attente qui sont disponibles pour traiter des connexions entrantes sur le service.</span><span class="sxs-lookup"><span data-stu-id="e92c1-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="e92c1-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e92c1-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="e92c1-134">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="e92c1-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e92c1-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-136">Nombre maximal de connexions en attente.</span><span class="sxs-lookup"><span data-stu-id="e92c1-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="e92c1-137">TransferMode</span><span class="sxs-lookup"><span data-stu-id="e92c1-137">TransferMode</span></span>  
 <span data-ttu-id="e92c1-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="e92c1-138">Data type: string</span></span>  
  
 <span data-ttu-id="e92c1-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="e92c1-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e92c1-140">Valeur qui spécifie si les messages sont mis en mémoire tampon ou transmis en continu par le transport orienté connexion.</span><span class="sxs-lookup"><span data-stu-id="e92c1-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e92c1-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e92c1-141">Requirements</span></span>  
  
|<span data-ttu-id="e92c1-142">MOF</span><span class="sxs-lookup"><span data-stu-id="e92c1-142">MOF</span></span>|<span data-ttu-id="e92c1-143">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e92c1-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e92c1-144">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e92c1-144">Namespace</span></span>|<span data-ttu-id="e92c1-145">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e92c1-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e92c1-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e92c1-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
