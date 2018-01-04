---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="28790-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="28790-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="28790-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="28790-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28790-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28790-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="28790-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="28790-105">Methods</span></span>  
 <span data-ttu-id="28790-106">La classe PeerTransportBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="28790-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28790-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="28790-107">Properties</span></span>  
 <span data-ttu-id="28790-108">La classe PeerTransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="28790-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="28790-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="28790-109">ListenIPAddress</span></span>  
 <span data-ttu-id="28790-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="28790-110">Data type: string</span></span>  
  
 <span data-ttu-id="28790-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="28790-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28790-112">Adresse IP sur laquelle le nœud homologue écoute les messages.</span><span class="sxs-lookup"><span data-stu-id="28790-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="28790-113">Port</span><span class="sxs-lookup"><span data-stu-id="28790-113">Port</span></span>  
 <span data-ttu-id="28790-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="28790-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="28790-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="28790-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28790-116">Port d’interface de réseau sur lequel la liaison traite les messages de canaux homologues.</span><span class="sxs-lookup"><span data-stu-id="28790-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="28790-117">Sécurité</span><span class="sxs-lookup"><span data-stu-id="28790-117">Security</span></span>  
 <span data-ttu-id="28790-118">Type de données : PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="28790-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="28790-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="28790-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28790-120">Paramètres de sécurité de transport de l'homologue.</span><span class="sxs-lookup"><span data-stu-id="28790-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28790-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="28790-121">Requirements</span></span>  
  
|<span data-ttu-id="28790-122">MOF</span><span class="sxs-lookup"><span data-stu-id="28790-122">MOF</span></span>|<span data-ttu-id="28790-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="28790-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="28790-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="28790-124">Namespace</span></span>|<span data-ttu-id="28790-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="28790-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28790-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28790-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
