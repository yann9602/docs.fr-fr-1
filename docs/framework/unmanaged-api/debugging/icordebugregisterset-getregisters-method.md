---
title: "ICorDebugRegisterSet::GetRegisters, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ddefb1ac5694bf1f213dd77e0ffc7f746b7e62cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="b0ce0-102">ICorDebugRegisterSet::GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="b0ce0-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="b0ce0-103">Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) qui est spécifié par le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ce0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0ce0-104">Syntax</span></span>  
  
```  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0ce0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0ce0-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="b0ce0-106">[in] Un masque de bits qui spécifie les valeurs de registres à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="b0ce0-107">Chaque bit correspond à un Registre.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="b0ce0-108">Si un bit est défini à un, la valeur de Registre est récupérée ; Sinon, la valeur de Registre n’est pas récupérée.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="b0ce0-109">[in] Le nombre de valeurs de Registre doit être récupéré.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="b0ce0-110">[out] Un tableau de `CORDB_REGISTER` objets, chacun d’eux reçoit une valeur d’un Registre.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0ce0-111">Notes</span><span class="sxs-lookup"><span data-stu-id="b0ce0-111">Remarks</span></span>  
 <span data-ttu-id="b0ce0-112">La taille du tableau doit être égale au nombre de bits définis sur un dans le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="b0ce0-113">Le `regCount` paramètre spécifie le nombre d’éléments dans la mémoire tampon qui reçoit les valeurs de Registre.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="b0ce0-114">Si le `regCount` valeur est trop petite pour le nombre de registres indiqué par le masque, les plus élevées des registres sont tronquées de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="b0ce0-115">Si le `regCount` valeur est trop grande, non `regBuffer` éléments ne sont pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="b0ce0-116">Si le masque de bits spécifie un Registre qui n’est pas disponible, `GetRegisters` retourne une valeur indéterminée pour ce Registre.</span><span class="sxs-lookup"><span data-stu-id="b0ce0-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ce0-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b0ce0-117">Requirements</span></span>  
 <span data-ttu-id="b0ce0-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0ce0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ce0-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0ce0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0ce0-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0ce0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0ce0-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ce0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ce0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0ce0-122">See Also</span></span>  
 [<span data-ttu-id="b0ce0-123">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="b0ce0-123">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="b0ce0-124">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="b0ce0-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
