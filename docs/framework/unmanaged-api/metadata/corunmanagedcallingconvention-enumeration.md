---
title: "CorUnmanagedCallingConvention, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorUnmanagedCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorUnmanagedCallingConvention
helpviewer_keywords: CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 446a948c8809d9f098ede8fbb9b426f6169ce812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="6aff0-102">CorUnmanagedCallingConvention, énumération</span><span class="sxs-lookup"><span data-stu-id="6aff0-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="6aff0-103">Spécifie les conventions d’appel du code non managé.</span><span class="sxs-lookup"><span data-stu-id="6aff0-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aff0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6aff0-104">Syntax</span></span>  
  
```  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="6aff0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6aff0-105">Members</span></span>  
  
|<span data-ttu-id="6aff0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6aff0-106">Member</span></span>|<span data-ttu-id="6aff0-107">Description</span><span class="sxs-lookup"><span data-stu-id="6aff0-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="6aff0-108">La convention d’appel langage C.</span><span class="sxs-lookup"><span data-stu-id="6aff0-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="6aff0-109">La convention d’appel standard.</span><span class="sxs-lookup"><span data-stu-id="6aff0-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="6aff0-110">« Thie » convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="6aff0-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="6aff0-111">La convention d’appel « rapide ».</span><span class="sxs-lookup"><span data-stu-id="6aff0-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="6aff0-112">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="6aff0-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="6aff0-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="6aff0-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="6aff0-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="6aff0-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="6aff0-115">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="6aff0-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6aff0-116">Notes</span><span class="sxs-lookup"><span data-stu-id="6aff0-116">Remarks</span></span>  
 <span data-ttu-id="6aff0-117">Le CLR ne prend pas en charge la convention d’appel « rapide » dans le .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="6aff0-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aff0-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6aff0-118">Requirements</span></span>  
 <span data-ttu-id="6aff0-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aff0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aff0-120">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6aff0-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6aff0-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aff0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aff0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6aff0-122">See Also</span></span>  
 [<span data-ttu-id="6aff0-123">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6aff0-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
