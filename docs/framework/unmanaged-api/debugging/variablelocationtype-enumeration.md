---
title: "Énumération de VariableLocationType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: VariableLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: VariableLocationType
helpviewer_keywords: VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0338a89acdd9c29370bc8e52ed9a099e9330c2cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="5a3f0-102">Énumération de VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="5a3f0-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="5a3f0-103">Indique le type d’emplacement native d’une variable.</span><span class="sxs-lookup"><span data-stu-id="5a3f0-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a3f0-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="5a3f0-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5a3f0-105">Members</span></span>  
  
|<span data-ttu-id="5a3f0-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5a3f0-106">Member</span></span>|<span data-ttu-id="5a3f0-107">Description</span><span class="sxs-lookup"><span data-stu-id="5a3f0-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="5a3f0-108">La variable est dans un Registre.</span><span class="sxs-lookup"><span data-stu-id="5a3f0-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="5a3f0-109">La variable est dans un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="5a3f0-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="5a3f0-110">La variable n’est pas stockée dans un Registre ou un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="5a3f0-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a3f0-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a3f0-111">Remarks</span></span>  
 <span data-ttu-id="5a3f0-112">Un membre de la `VariableLocationType` énumération retournée par le [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="5a3f0-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a3f0-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5a3f0-113">Requirements</span></span>  
 <span data-ttu-id="5a3f0-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a3f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a3f0-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a3f0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a3f0-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a3f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a3f0-117">**Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a3f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a3f0-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a3f0-118">See Also</span></span>  
 [<span data-ttu-id="5a3f0-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="5a3f0-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
