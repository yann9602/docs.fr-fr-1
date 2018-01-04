---
title: "CorEventAttr, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorEventAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorEventAttr
helpviewer_keywords: CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4302ff7627bf5e06f3c1b1263ec38a31393d411
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="cc3c8-102">CorEventAttr, énumération</span><span class="sxs-lookup"><span data-stu-id="cc3c8-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="cc3c8-103">Contient des valeurs qui décrivent les métadonnées d'un événement.</span><span class="sxs-lookup"><span data-stu-id="cc3c8-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc3c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc3c8-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="cc3c8-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cc3c8-105">Members</span></span>  
  
|<span data-ttu-id="cc3c8-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cc3c8-106">Member</span></span>|<span data-ttu-id="cc3c8-107">Description</span><span class="sxs-lookup"><span data-stu-id="cc3c8-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="cc3c8-108">Spécifie que l’événement est spécial, et que son nom décrit comment.</span><span class="sxs-lookup"><span data-stu-id="cc3c8-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="cc3c8-109">Réservé à un usage interne par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="cc3c8-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="cc3c8-110">Spécifie que le common language runtime doit vérifier l’encodage du nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="cc3c8-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc3c8-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cc3c8-111">Requirements</span></span>  
 <span data-ttu-id="cc3c8-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc3c8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc3c8-113">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cc3c8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cc3c8-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc3c8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3c8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc3c8-115">See Also</span></span>  
 [<span data-ttu-id="cc3c8-116">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="cc3c8-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
