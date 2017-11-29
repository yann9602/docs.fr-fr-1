---
title: "CorDebugHandleType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugHandleType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugHandleType
helpviewer_keywords: CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef0b892d8dc277286114e8f9eda8d0f16833e1d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="37c3e-102">CorDebugHandleType, énumération</span><span class="sxs-lookup"><span data-stu-id="37c3e-102">CorDebugHandleType Enumeration</span></span>
<span data-ttu-id="37c3e-103">Indique le type de handle.</span><span class="sxs-lookup"><span data-stu-id="37c3e-103">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37c3e-104">Syntax</span></span>  
  
```  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="37c3e-105">Membres</span><span class="sxs-lookup"><span data-stu-id="37c3e-105">Members</span></span>  
  
|<span data-ttu-id="37c3e-106">Membre</span><span class="sxs-lookup"><span data-stu-id="37c3e-106">Member</span></span>|<span data-ttu-id="37c3e-107">Description</span><span class="sxs-lookup"><span data-stu-id="37c3e-107">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="37c3e-108">Le handle est fort, ce qui empêche un objet d’être récupéré par le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="37c3e-108">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="37c3e-109">Le handle est faible, ce qui n’empêche pas un objet d’être récupéré par le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="37c3e-109">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="37c3e-110">Le handle n’est plus valide lorsque l’objet est collecté.</span><span class="sxs-lookup"><span data-stu-id="37c3e-110">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37c3e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="37c3e-111">Requirements</span></span>  
 <span data-ttu-id="37c3e-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37c3e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c3e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37c3e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37c3e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37c3e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37c3e-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c3e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37c3e-116">See Also</span></span>  
 [<span data-ttu-id="37c3e-117">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="37c3e-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
