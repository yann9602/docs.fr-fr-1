---
title: "ICorDebugMergedAssemblyRecord::GetVersion, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 68fa2b1b7502f13876c6e613f012a0c78ab7c5d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="bc659-102">ICorDebugMergedAssemblyRecord::GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="bc659-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="bc659-103">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="bc659-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc659-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc659-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc659-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc659-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="bc659-106">[out] Pointeur vers le numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="bc659-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="bc659-107">[out] Pointeur vers le numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="bc659-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="bc659-108">[out] Pointeur vers le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="bc659-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="bc659-109">[out] Pointeur vers le numéro de révision.</span><span class="sxs-lookup"><span data-stu-id="bc659-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc659-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="bc659-110">Remarks</span></span>  
 <span data-ttu-id="bc659-111">Pour plus d'informations sur les numéros de version d'assembly, consultez la rubrique de la classe <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="bc659-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc659-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bc659-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc659-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bc659-113">Requirements</span></span>  
 <span data-ttu-id="bc659-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc659-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc659-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc659-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc659-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc659-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc659-117">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc659-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc659-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc659-118">See Also</span></span>  
 [<span data-ttu-id="bc659-119">Icordebugmergedassemblyrecord, Interface</span><span class="sxs-lookup"><span data-stu-id="bc659-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="bc659-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="bc659-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
