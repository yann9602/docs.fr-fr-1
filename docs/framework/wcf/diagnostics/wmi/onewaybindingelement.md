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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43707f25a9ee1beb1ce7adac36a2c4a55cab6d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="6119a-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6119a-102">OneWayBindingElement</span></span>
<span data-ttu-id="6119a-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="6119a-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6119a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6119a-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6119a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6119a-105">Methods</span></span>  
 <span data-ttu-id="6119a-106">La classe OneWayBindingElement ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="6119a-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6119a-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="6119a-107">Properties</span></span>  
 <span data-ttu-id="6119a-108">La classe OneWayBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="6119a-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="6119a-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6119a-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="6119a-110">Type de données : ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="6119a-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="6119a-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6119a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6119a-112">Paramètres du pool de canaux.</span><span class="sxs-lookup"><span data-stu-id="6119a-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="6119a-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="6119a-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="6119a-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="6119a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="6119a-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6119a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6119a-116">Nombre maximal de canaux acceptés.</span><span class="sxs-lookup"><span data-stu-id="6119a-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="6119a-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="6119a-117">PacketRoutable</span></span>  
 <span data-ttu-id="6119a-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="6119a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6119a-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="6119a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6119a-120">Valeur qui indique si le paquet peut être routé.</span><span class="sxs-lookup"><span data-stu-id="6119a-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6119a-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6119a-121">Requirements</span></span>  
  
|<span data-ttu-id="6119a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6119a-122">MOF</span></span>|<span data-ttu-id="6119a-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6119a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6119a-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="6119a-124">Namespace</span></span>|<span data-ttu-id="6119a-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6119a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6119a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6119a-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
