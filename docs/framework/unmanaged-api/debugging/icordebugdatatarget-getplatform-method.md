---
title: "ICorDebugDataTarget::GetPlatform, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetPlatform Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf2f852d0da36211e379a4068cccff9dfc656100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="6b94b-102">ICorDebugDataTarget::GetPlatform, méthode</span><span class="sxs-lookup"><span data-stu-id="6b94b-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="6b94b-103">Fournit des informations sur la plateforme, notamment l’architecture de processeur et de système d’exploitation, sur lequel s’exécute le processus cible.</span><span class="sxs-lookup"><span data-stu-id="6b94b-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b94b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b94b-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b94b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b94b-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="6b94b-106">[out] Un pointeur vers un [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) énumération qui décrit la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="6b94b-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b94b-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="6b94b-107">Remarks</span></span>  
 <span data-ttu-id="6b94b-108">Le `CorDebugPlatformEnum` valeur de retour d’énumération est utilisée par le [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface pour déterminer les détails du processus cible tels que sa taille du pointeur disposition de l’espace adresse, jeu de Registre, format de l’instruction, mise en page du contexte, et conventions d’appel.</span><span class="sxs-lookup"><span data-stu-id="6b94b-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="6b94b-109">Le `pTargetPlatform` valeur peut faire référence à une plateforme émulée pour la cible au lieu de spécifier le matériel en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="6b94b-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="6b94b-110">Par exemple, un processus qui s’exécute dans l’environnement Windows on Windows (WOW) sur une édition 64 bits du système d’exploitation Windows doit utiliser le `CORDB_PLATFORM_WINDOWS_X86` valeur de la [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="6b94b-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="6b94b-111">Cette méthode doit réussir.</span><span class="sxs-lookup"><span data-stu-id="6b94b-111">This method must succeed.</span></span> <span data-ttu-id="6b94b-112">En cas d’échec, la plateforme cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="6b94b-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="6b94b-113">La méthode peut échouer pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="6b94b-113">The method may fail for the following reasons:</span></span>  
  
-   <span data-ttu-id="6b94b-114">La plateforme émulée pour la cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="6b94b-114">The platform that is being emulated for the target is unusable.</span></span>  
  
-   <span data-ttu-id="6b94b-115">Le matériel sur la plateforme cible est inutilisable.</span><span class="sxs-lookup"><span data-stu-id="6b94b-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b94b-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6b94b-116">Requirements</span></span>  
 <span data-ttu-id="6b94b-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b94b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b94b-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b94b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b94b-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b94b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b94b-120">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b94b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b94b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b94b-121">See Also</span></span>  
 [<span data-ttu-id="6b94b-122">ICorDebugDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="6b94b-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="6b94b-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6b94b-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6b94b-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="6b94b-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
