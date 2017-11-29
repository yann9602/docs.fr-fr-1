---
title: ReliableSessionBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f4aff60c96db5071d41a3f011019b05746f0c96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="a605f-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="a605f-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="a605f-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="a605f-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a605f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a605f-104">Syntax</span></span>  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a605f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a605f-105">Methods</span></span>  
 <span data-ttu-id="a605f-106">La classe ReliableSessionBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="a605f-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a605f-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a605f-107">Properties</span></span>  
 <span data-ttu-id="a605f-108">La classe ReliableSessionBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="a605f-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="a605f-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="a605f-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="a605f-110">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="a605f-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="a605f-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-112">Intervalle d'attente d'une destination avant l'envoi d'un accusé de réception à la source de message sur les canaux fiables créés par la fabrique.</span><span class="sxs-lookup"><span data-stu-id="a605f-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="a605f-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="a605f-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="a605f-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="a605f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a605f-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-116">Valeur booléenne qui spécifie si le contrôle de flux est activé.</span><span class="sxs-lookup"><span data-stu-id="a605f-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="a605f-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="a605f-117">InactivityTimeout</span></span>  
 <span data-ttu-id="a605f-118">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="a605f-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="a605f-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-120">Spécifie la durée maximale pendant laquelle le canal va laisser l'autre partie communicante ne pas envoyer des messages avant de provoquer une erreur sur le canal.</span><span class="sxs-lookup"><span data-stu-id="a605f-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="a605f-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="a605f-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="a605f-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="a605f-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="a605f-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-124">Nombre maximal de canaux qui peuvent attendre d'être acceptés sur l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="a605f-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="a605f-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="a605f-125">MaxRetryCount</span></span>  
 <span data-ttu-id="a605f-126">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="a605f-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="a605f-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-128">Nombre maximal de tentatives qu'un canal fiable peut effectuer pour retransmettre un message dont il n'a pas reçu d'accusé de réception, en appelant `Send` sur son canal sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="a605f-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="a605f-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="a605f-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="a605f-130">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="a605f-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="a605f-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-132">Taille de fenêtre de transfert maximale pour la session fiable.</span><span class="sxs-lookup"><span data-stu-id="a605f-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="a605f-133">Ordered</span><span class="sxs-lookup"><span data-stu-id="a605f-133">Ordered</span></span>  
 <span data-ttu-id="a605f-134">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="a605f-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="a605f-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-136">Valeur booléenne qui spécifie si l'arrivée de messages est garantie dans leur ordre d'envoi.</span><span class="sxs-lookup"><span data-stu-id="a605f-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="a605f-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="a605f-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="a605f-138">Type de données : entier</span><span class="sxs-lookup"><span data-stu-id="a605f-138">Data type: integer</span></span>  
  
 <span data-ttu-id="a605f-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="a605f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a605f-140">Entier qui spécifie la version du protocole WS-ReliableMessaging utilisée dans la session fiable.</span><span class="sxs-lookup"><span data-stu-id="a605f-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a605f-141">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a605f-141">Requirements</span></span>  
  
|<span data-ttu-id="a605f-142">MOF</span><span class="sxs-lookup"><span data-stu-id="a605f-142">MOF</span></span>|<span data-ttu-id="a605f-143">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a605f-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a605f-144">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="a605f-144">Namespace</span></span>|<span data-ttu-id="a605f-145">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a605f-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a605f-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a605f-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
