---
title: "CorDebugJITCompilerFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugJITCompilerFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugJITCompilerFlags
helpviewer_keywords: CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d7eb8421dcd68c67536e0de038f7038500556c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="e983c-102">CorDebugJITCompilerFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="e983c-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="e983c-103">Contient des valeurs qui influencent le comportement du compilateur juste-à-temps managé.</span><span class="sxs-lookup"><span data-stu-id="e983c-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e983c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e983c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="e983c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e983c-105">Members</span></span>  
  
|<span data-ttu-id="e983c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e983c-106">Member</span></span>|<span data-ttu-id="e983c-107">Description</span><span class="sxs-lookup"><span data-stu-id="e983c-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="e983c-108">Spécifie que le compilateur doit suivre des données de compilation et autorise les optimisations.</span><span class="sxs-lookup"><span data-stu-id="e983c-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="e983c-109">Spécifie que le compilateur doit suivre des données de compilation, mais désactive les optimisations.</span><span class="sxs-lookup"><span data-stu-id="e983c-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="e983c-110">Spécifie que le compilateur doit suivre des données de compilation, désactive les optimisations, et permet aux technologies Modifier & Continue.</span><span class="sxs-lookup"><span data-stu-id="e983c-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e983c-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e983c-111">Requirements</span></span>  
 <span data-ttu-id="e983c-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e983c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e983c-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e983c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e983c-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e983c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e983c-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e983c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e983c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e983c-116">See Also</span></span>  
 [<span data-ttu-id="e983c-117">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="e983c-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
