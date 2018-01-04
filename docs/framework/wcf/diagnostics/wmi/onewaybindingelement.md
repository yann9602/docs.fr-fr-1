---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="09902-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="09902-102">OneWayBindingElement</span></span>
<span data-ttu-id="09902-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="09902-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09902-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09902-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="09902-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="09902-105">Methods</span></span>  
 <span data-ttu-id="09902-106">La classe OneWayBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="09902-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="09902-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="09902-107">Properties</span></span>  
 <span data-ttu-id="09902-108">La classe OneWayBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="09902-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="09902-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="09902-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="09902-110">Type de données : ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="09902-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="09902-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="09902-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09902-112">Paramètres du pool de canaux.</span><span class="sxs-lookup"><span data-stu-id="09902-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="09902-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="09902-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="09902-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="09902-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="09902-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="09902-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09902-116">Nombre maximal de canaux acceptés.</span><span class="sxs-lookup"><span data-stu-id="09902-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="09902-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="09902-117">PacketRoutable</span></span>  
 <span data-ttu-id="09902-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="09902-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="09902-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="09902-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09902-120">Valeur qui indique si le paquet peut être routé.</span><span class="sxs-lookup"><span data-stu-id="09902-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09902-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09902-121">Requirements</span></span>  
  
|<span data-ttu-id="09902-122">MOF</span><span class="sxs-lookup"><span data-stu-id="09902-122">MOF</span></span>|<span data-ttu-id="09902-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="09902-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="09902-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="09902-124">Namespace</span></span>|<span data-ttu-id="09902-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="09902-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09902-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09902-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
