---
title: "CorSetENC, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSetENC
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSetENC
helpviewer_keywords: CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85a909d92be8bfdb9ada709b54cf252183ff411e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="c766d-102">CorSetENC, énumération</span><span class="sxs-lookup"><span data-stu-id="c766d-102">CorSetENC Enumeration</span></span>
<span data-ttu-id="c766d-103">Contient des valeurs utilisées pour influencer le comportement pendant la génération de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c766d-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c766d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c766d-104">Syntax</span></span>  
  
```  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="c766d-105">Membres</span><span class="sxs-lookup"><span data-stu-id="c766d-105">Members</span></span>  
  
|<span data-ttu-id="c766d-106">Membre</span><span class="sxs-lookup"><span data-stu-id="c766d-106">Member</span></span>|<span data-ttu-id="c766d-107">Description</span><span class="sxs-lookup"><span data-stu-id="c766d-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="c766d-108">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="c766d-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="c766d-109">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="c766d-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="c766d-110">Indique que tandis que les métadonnées peuvent être mis à jour, les jetons ne peut pas être déplacés.</span><span class="sxs-lookup"><span data-stu-id="c766d-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="c766d-111">Indique que les jetons peuvent être déplacés pendant les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="c766d-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="c766d-112">Indique que les mises à jour peuvent comporter que des ajouts.</span><span class="sxs-lookup"><span data-stu-id="c766d-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="c766d-113">Les jetons ne peut pas être déplacés.</span><span class="sxs-lookup"><span data-stu-id="c766d-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="c766d-114">Indique que la compilation est incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="c766d-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="c766d-115">Indique que seules les métadonnées modifiées doivent être enregistrées.</span><span class="sxs-lookup"><span data-stu-id="c766d-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="c766d-116">Inclut `MDUpdateENC`, `MDUpdateFull` et `MDUpdateIncremental`.</span><span class="sxs-lookup"><span data-stu-id="c766d-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c766d-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c766d-117">Requirements</span></span>  
 <span data-ttu-id="c766d-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c766d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c766d-119">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c766d-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c766d-120">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c766d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c766d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c766d-121">See Also</span></span>  
 [<span data-ttu-id="c766d-122">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c766d-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
