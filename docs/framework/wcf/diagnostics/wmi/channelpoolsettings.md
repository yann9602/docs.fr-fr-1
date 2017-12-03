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
ms.openlocfilehash: e97e934673efbc6d0f72751c7cb1de6fba84a141
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="3161b-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3161b-102">ChannelPoolSettings</span></span>
<span data-ttu-id="3161b-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3161b-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3161b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3161b-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3161b-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3161b-105">Methods</span></span>  
 <span data-ttu-id="3161b-106">La classe ChannelPoolSettings ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="3161b-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3161b-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3161b-107">Properties</span></span>  
 <span data-ttu-id="3161b-108">La classe ChannelPoolSettings a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="3161b-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="3161b-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="3161b-109">IdleTimeout</span></span>  
 <span data-ttu-id="3161b-110">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="3161b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="3161b-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3161b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3161b-112">Période maximale d'inactivité de la connexion au terme de laquelle la connexion est coupée.</span><span class="sxs-lookup"><span data-stu-id="3161b-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="3161b-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="3161b-113">LeaseTimeout</span></span>  
 <span data-ttu-id="3161b-114">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="3161b-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="3161b-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3161b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3161b-116">Période maximale d'exécution d'une opération de bail avant expiration du délai d'attente.</span><span class="sxs-lookup"><span data-stu-id="3161b-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="3161b-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="3161b-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="3161b-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="3161b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="3161b-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3161b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3161b-120">Nombre maximal de canaux sortants pour chaque point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3161b-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3161b-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3161b-121">Requirements</span></span>  
  
|<span data-ttu-id="3161b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3161b-122">MOF</span></span>|<span data-ttu-id="3161b-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3161b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3161b-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="3161b-124">Namespace</span></span>|<span data-ttu-id="3161b-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3161b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3161b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3161b-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
