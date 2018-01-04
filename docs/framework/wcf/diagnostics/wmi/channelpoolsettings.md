---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3995b517b27a5565f7fcb9c11da27c9e1bb40887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="7f808-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7f808-102">ChannelPoolSettings</span></span>
<span data-ttu-id="7f808-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7f808-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f808-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f808-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7f808-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7f808-105">Methods</span></span>  
 <span data-ttu-id="7f808-106">La classe ChannelPoolSettings ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="7f808-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7f808-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7f808-107">Properties</span></span>  
 <span data-ttu-id="7f808-108">La classe ChannelPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="7f808-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="7f808-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="7f808-109">IdleTimeout</span></span>  
 <span data-ttu-id="7f808-110">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="7f808-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="7f808-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f808-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f808-112">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="7f808-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="7f808-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="7f808-113">LeaseTimeout</span></span>  
 <span data-ttu-id="7f808-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="7f808-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="7f808-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f808-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f808-116">Période maximale d'exécution d'une opération de bail avant expiration du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="7f808-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="7f808-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="7f808-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="7f808-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="7f808-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="7f808-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f808-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f808-120">Nombre maximal de canaux sortants pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7f808-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f808-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7f808-121">Requirements</span></span>  
  
|<span data-ttu-id="7f808-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7f808-122">MOF</span></span>|<span data-ttu-id="7f808-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7f808-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7f808-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="7f808-124">Namespace</span></span>|<span data-ttu-id="7f808-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7f808-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f808-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f808-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
