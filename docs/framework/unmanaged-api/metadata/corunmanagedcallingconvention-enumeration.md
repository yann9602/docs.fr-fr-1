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
ms.openlocfilehash: f66cb036de8450d4c1b3431b92487260956d47f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="3db42-102">CorUnmanagedCallingConvention, énumération</span><span class="sxs-lookup"><span data-stu-id="3db42-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="3db42-103">Spécifie les conventions d’appel du code non managé.</span><span class="sxs-lookup"><span data-stu-id="3db42-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3db42-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3db42-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3db42-105">Members</span></span>  
  
|<span data-ttu-id="3db42-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3db42-106">Member</span></span>|<span data-ttu-id="3db42-107">Description</span><span class="sxs-lookup"><span data-stu-id="3db42-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="3db42-108">La convention d’appel langage C.</span><span class="sxs-lookup"><span data-stu-id="3db42-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="3db42-109">La convention d’appel standard.</span><span class="sxs-lookup"><span data-stu-id="3db42-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="3db42-110">« Thie » convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="3db42-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="3db42-111">La convention d’appel « rapide ».</span><span class="sxs-lookup"><span data-stu-id="3db42-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="3db42-112">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="3db42-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="3db42-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="3db42-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="3db42-114">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="3db42-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="3db42-115">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="3db42-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3db42-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="3db42-116">Remarks</span></span>  
 <span data-ttu-id="3db42-117">Le CLR ne prend pas en charge la convention d’appel « rapide » dans le .NET Framework version 1.0.</span><span class="sxs-lookup"><span data-stu-id="3db42-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db42-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3db42-118">Requirements</span></span>  
 <span data-ttu-id="3db42-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db42-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db42-120">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3db42-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3db42-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db42-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db42-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3db42-122">See Also</span></span>  
 [<span data-ttu-id="3db42-123">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3db42-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
