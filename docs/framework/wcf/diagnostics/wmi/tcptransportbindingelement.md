---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="6c7b1-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6c7b1-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="6c7b1-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6c7b1-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c7b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c7b1-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6c7b1-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6c7b1-105">Methods</span></span>  
 <span data-ttu-id="6c7b1-106">La classe TcpTransportBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="6c7b1-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6c7b1-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6c7b1-107">Properties</span></span>  
 <span data-ttu-id="6c7b1-108">La classe TcpTransportBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c7b1-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="6c7b1-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6c7b1-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="6c7b1-110">Type de données : TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6c7b1-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="6c7b1-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6c7b1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c7b1-112">Paramètres de pool de connexions.</span><span class="sxs-lookup"><span data-stu-id="6c7b1-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="6c7b1-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="6c7b1-113">ListenBacklog</span></span>  
 <span data-ttu-id="6c7b1-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="6c7b1-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6c7b1-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6c7b1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c7b1-116">Nombre maximal de demandes de connexion en file d'attente pouvant être en attente.</span><span class="sxs-lookup"><span data-stu-id="6c7b1-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="6c7b1-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="6c7b1-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="6c7b1-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="6c7b1-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c7b1-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6c7b1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c7b1-120">Valeur booléenne qui spécifie si le partage de port TCP est activé pour cette connexion.</span><span class="sxs-lookup"><span data-stu-id="6c7b1-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="6c7b1-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="6c7b1-121">TeredoEnabled</span></span>  
 <span data-ttu-id="6c7b1-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="6c7b1-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c7b1-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6c7b1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c7b1-124">Valeur booléenne qui spécifie si Teredo (technologie d'adressage de clients placés derrière des pare-feu) est activé.</span><span class="sxs-lookup"><span data-stu-id="6c7b1-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c7b1-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6c7b1-125">Requirements</span></span>  
  
|<span data-ttu-id="6c7b1-126">MOF</span><span class="sxs-lookup"><span data-stu-id="6c7b1-126">MOF</span></span>|<span data-ttu-id="6c7b1-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6c7b1-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6c7b1-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="6c7b1-128">Namespace</span></span>|<span data-ttu-id="6c7b1-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6c7b1-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c7b1-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c7b1-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
